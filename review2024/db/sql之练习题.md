本文章来源于：<https://github.com/Zeb-D/my-review> ，请star 强力支持，你的支持，就是我的动力。

[TOC]

基本表结构：

```mysql
student(sno,sname,sage,ssex)学生表
course(cno,cname,tno) 课程表
sc(sno,cno,score) 成绩表

teacher(tno,tname) 教师表

```

1、查询课程1的成绩比课程2的成绩高的所有学生的学号

> select a.sno from (select sno,score from sc where cno=1) a, (select sno,score from sc where cno=2) b where a.score>b.score and a.sno=b.sno 



2，查询平均成绩大于60分的同学的学号和平均成绩 

select a.sno as "学号", avg(a.score) as "平均成绩"  from (select sno,score from sc) a  group by sno having avg(a.score)>60    

3，查询所有同学的学号、姓名、选课数、总成绩 

select a.sno as 学号, b.sname as 姓名, count(a.cno) as 选课数, sum(a.score) as 总成绩 from sc a, student b where a.sno = b.sno group by a.sno, b.sname  或者：  selectstudent.sno as 学号, student.sname as 姓名,  count(sc.cno) as 选课数, sum(score) as 总成绩 from student left Outer join sc on student.sno = sc.sno group by student.sno, sname  

4，查询姓“张”的老师的个数  

selectcount(distinct(tname)) from teacher where tname like '张%‘ 或者： select tname as "姓名", count(distinct(tname)) as "人数"  from teacher  where tname like'张%' group by tname    

5，查询没学过“张三”老师课的同学的学号、姓名 

select student.sno,student.sname from student where sno not in (select distinct(sc.sno) from sc,course,teacher where sc.cno=course.cno and teacher.tno=course.tno and teacher.tname='张三')    

6，查询同时学过课程1和课程2的同学的学号、姓名 select sno, sname from student where sno in (select sno from sc where sc.cno = 1) and sno in (select sno from sc where sc.cno = 2) 或者：  selectc.sno, c.sname from (select sno from sc where sc.cno = 1) a, (select sno from sc where sc.cno = 2) b, student c where a.sno = b.sno and a.sno = c.sno 或者：  select student.sno,student.sname from student,sc where student.sno=sc.sno and sc.cno=1 and exists( select * from sc as sc_2 where sc_2.sno=sc.sno and sc_2.cno=2)    

7，查询学过“李四”老师所教所有课程的所有同学的学号、姓名 

select a.sno, a.sname from student a, sc b where a.sno = b.sno and b.cno in (select c.cno from course c, teacher d where c.tno = d.tno and d.tname = '李四')  或者：  select a.sno, a.sname from student a, sc b, (select c.cno from course c, teacher d where c.tno = d.tno and d.tname = '李四') e where a.sno = b.sno and b.cno = e.cno    

8，查询课程编号1的成绩比课程编号2的成绩高的所有同学的学号、姓名

 select a.sno, a.sname from student a, (select sno, score from sc where cno = 1) b, (select sno, score from sc where cno = 2) c where b.score > c.score and b.sno = c.sno and a.sno = b.sno    

9，查询所有课程成绩小于60分的同学的学号、姓名 

select sno,sname from student where sno not in (select distinct sno from sc where score > 60)    

10，查询至少有一门课程与学号为1的同学所学课程相同的同学的学号和姓名

 select distinct a.sno, a.sname from student a, sc b where a.sno <> 1 and a.sno=b.sno and b.cno in (select cno from sc where sno = 1)  

或者：  select s.sno,s.sname  from student s, (select sc.sno  from sc where sc.cno in (select sc1.cno from sc sc1 where sc1.sno=1)and sc.sno<>1 group by sc.sno)r1 where r1.sno=s.sno  

11、把“sc”表中“王五”所教课的成绩都更改为此课程的平均成绩

 update sc set score = (select avg(sc_2.score) from sc sc_2 wheresc_2.cno=sc.cno) from course,teacher where course.cno=sc.cno and course.tno=teacher.tno andteacher.tname='王五'   

12、查询和编号为2的同学学习的课程完全相同的其他同学学号和姓名 这一题分两步查：  

> 1，  select sno from sc where sno <> 2 group by sno having sum(cno) = (select sum(cno) from sc where sno = 2) 
>
>  2， select b.sno, b.sname from sc a, student b where b.sno <> 2 and a.sno = b.sno group by b.sno, b.sname having sum(cno) = (select sum(cno) from sc where sno = 2)  

13、删除学习“王五”老师课的sc表记录 

delete sc from course, teacher where course.cno = sc.cno and course.tno = teacher.tno and tname = '王五'  14、向sc表中插入一些记录，这些记录要求符合以下条件：

 将没有课程3成绩同学的该成绩补齐, 其成绩取所有学生的课程2的平均成绩

 insert sc select sno, 3, (select avg(score) from sc where cno = 2) from student where sno not in (select sno from sc where cno = 3)  

15、按平平均分从高到低显示所有学生的如下统计报表： 

-- 学号,企业管理,马克思,UML,数据库,物理,课程数,平均分

 select sno as 学号 ,max(case when cno = 1 then score end) AS 企业管理 ,max(case when cno = 2 then score end) AS 马克思 ,max(case when cno = 3 then score end) AS UML ,max(case when cno = 4 then score end) AS 数据库 ,max(case when cno = 5 then score end) AS 物理 ,count(cno) AS 课程数 ,avg(score) AS 平均分 FROM sc GROUP by sno ORDER by avg(score) DESC  

16、查询各科成绩最高分和最低分： 

 以如下形式显示：课程号，最高分，最低分 

select cno as 课程号, max(score) as 最高分, min(score) 最低分 from sc group by cno  select  course.cno as '课程号' ,MAX(score) as '最高分' ,MIN(score) as '最低分' from sc,course where sc.cno=course.cno group by course.cno  

17、按各科平均成绩从低到高和及格率的百分数从高到低顺序

 SELECT t.cno AS 课程号, max(course.cname)AS 课程名, isnull(AVG(score),0) AS 平均成绩, 100 * SUM(CASE WHEN isnull(score,0)>=60 THEN 1 ELSE 0 END)/count(1) AS 及格率 FROM sc t, course where t.cno = course.cno GROUP BY t.cno ORDER BY 及格率 desc  

18、查询不同老师所教不同课程平均分, 从高到低显示 

select max(c.tname) as 教师, max(b.cname) 课程, avg(a.score) 平均分 from sc a, course b, teacher c where a.cno = b.cno and b.tno = c.tno group by a.cno order by 平均分 desc 

或者： select r.tname as '教师',r.rname as '课程' , AVG(score) as '平均分' from sc, (select  t.tname,c.cno as rcso,c.cname as rname from teacher t ,course c where t.tno=c.tno)r where sc.cno=r.rcso group by sc.cno,r.tname,r.rname  order by AVG(score) desc  

19、查询如下课程成绩均在第3名到第6名之间的学生的成绩：

 -- [学生ID],[学生姓名],企业管理,马克思,UML,数据库,平均成绩 

select top 6 max(a.sno) 学号, max(b.sname) 姓名, max(case when cno = 1 then score end) as 企业管理, max(case when cno = 2 then score end) as 马克思, max(case when cno = 3 then score end) as UML, max(case when cno = 4 then score end) as 数据库, avg(score) as 平均分 from sc a, student b where a.sno not in   (select top 2 sno from sc where cno = 1 order by score desc)   and a.sno not in (select top 2 sno from sc where cno = 2 order by scoredesc)   and a.sno not in (select top 2 sno from sc where cno = 3 order by scoredesc)   and a.sno not in (select top 2 sno from sc where cno = 4 order by scoredesc)   and a.sno = b.sno group by a.sno



