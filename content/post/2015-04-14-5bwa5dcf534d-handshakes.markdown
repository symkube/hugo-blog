---
author: 111qqz
date: 2015-04-14 20:40:00+00:00
draft: false
title: '[WA]cf 534 D. Handshakes'
type: post
url: /2015/04/wacf534d-handshakes/
categories:
- ACM
---
















D. Handshakes







time limit per test


1 second







memory limit per test


256 megabytes







input


standard input







output


standard output










On February, 30th _n_ students came in the Center for Training Olympiad Programmers (CTOP) of the Berland State University. They came one by one, one after another. Each of them went in, and before sitting down at his desk, greeted with those who were present in the room by shaking hands. Each of the students who came in stayed in CTOP until the end of the day and never left.




At any time any three students could join together and start participating in a team contest, which lasted until the end of the day. The team did not distract from the contest for a minute, so when another student came in and greeted those who were present, he did not shake hands with the members of the contest writing team. Each team consisted of exactly three students, and each student could not become a member of more than one team. Different teams could start writing contest at different times.




Given how many present people shook the hands of each student, get a possible order in which the students could have come to CTOP. If such an order does not exist, then print that this is impossible.




Please note that some students could work independently until the end of the day, without participating in a team contest.










Input




The first line contains integer _n_ (1 ≤ _n_ ≤ 2*105) -- the number of students who came to CTOP. The next line contains _n_ integers_a_1, _a_2, ..., _a__n_ (0 ≤ _a__i_ < _n_), where _a__i_ is the number of students with who the _i_-th student shook hands.










Output




If the sought order of students exists, print in the first line "Possible" and in the second line print the permutation of the students' numbers defining the order in which the students entered the center. Number _i_ that stands to the left of number _j_ in this permutation means that the _i_-th student came earlier than the _j_-th student. If there are multiple answers, print any of them.




If the sought order of students doesn't exist, in a single line print "Impossible".










Sample test(s)










input



    
    5<br></br>2 1 3 0 1










output



    
    Possible<br></br>4 5 1 3 2 










input



    
    9<br></br>0 2 3 4 1 1 0 2 2










output



    
    Possible<br></br>7 5 2 1 6 8 3 4 9










input



    
    4<br></br>0 2 1 1










output



    
    Impossible
















Note




In the first sample from the statement the order of events could be as follows:





  * student 4 comes in (_a_4 = 0), he has no one to greet;
  * student 5 comes in (_a_5 = 1), he shakes hands with student 4;
  * student 1 comes in (_a_1 = 2), he shakes hands with two students (students 4, 5);
  * student 3 comes in (_a_3 = 3), he shakes hands with three students (students 4, 5, 1);
  * students 4, 5, 3 form a team and start writing a contest;
  * student 2 comes in (_a_2 = 1), he shakes hands with one student (number 1).



In the second sample from the statement the order of events could be as follows:





  * student 7 comes in (_a_7 = 0), he has nobody to greet;
  * student 5 comes in (_a_5 = 1), he shakes hands with student 7;
  * student 2 comes in (_a_2 = 2), he shakes hands with two students (students 7, 5);
  * students 7, 5, 2 form a team and start writing a contest;
  * student 1 comes in(_a_1 = 0), he has no one to greet (everyone is busy with the contest);
  * student 6 comes in (_a_6 = 1), he shakes hands with student 1;
  * student 8 comes in (_a_8 = 2), he shakes hands with two students (students 1, 6);
  * student 3 comes in (_a_3 = 3), he shakes hands with three students (students 1, 6, 8);
  * student 4 comes in (_a_4 = 4), he shakes hands with four students (students 1, 6, 8, 3);
  * students 8, 3, 4 form a team and start writing a contest;
  * student 9 comes in (_a_9 = 2), he shakes hands with two students (students 1, 6).



In the third sample from the statement the order of events is restored unambiguously:





  * student 1 comes in (_a_1 = 0), he has no one to greet;
  * student 3 comes in (or student 4) (_a_3 = _a_4 = 1), he shakes hands with student 1;
  * student 2 comes in (_a_2 = 2), he shakes hands with two students (students 1, 3 (or 4));
  * the remaining student 4 (or student 3), must shake one student's hand (_a_3 = _a_4 = 1) but it is impossible as there are only two scenarios: either a team formed and he doesn't greet anyone, or he greets all the three present people who work individually.






WA#37了。。。感觉思路没有问题呀...就是纯模拟。以后再看。






    
    #include <iostream><span style="color: #000000;">
    #include </span><algorithm><span style="color: #000000;">
    #include </span><cstring><span style="color: #000000;">
    #include </span><cmath><span style="color: #000000;">
    #include </span><cstdio>
    <span style="color: #0000ff;">using</span> <span style="color: #0000ff;">namespace</span><span style="color: #000000;"> std;
    </span><span style="color: #0000ff;">const</span> <span style="color: #0000ff;">int</span> N=2e5+<span style="color: #800080;">7</span><span style="color: #000000;">;
    </span><span style="color: #0000ff;">int</span><span style="color: #000000;"> n,now;
    </span><span style="color: #0000ff;">int</span> a[N],b[N][<span style="color: #800080;">100</span><span style="color: #000000;">],p[N],ans[N];
    </span><span style="color: #0000ff;">int</span><span style="color: #000000;"> main()
    {
        cin</span>>><span style="color: #000000;">n;
        memset(b,</span><span style="color: #800080;">0</span>,<span style="color: #0000ff;">sizeof</span><span style="color: #000000;">(b));
        memset(p,</span><span style="color: #800080;">0</span>,<span style="color: #0000ff;">sizeof</span><span style="color: #000000;">(p));
        </span><span style="color: #0000ff;">for</span> ( <span style="color: #0000ff;">int</span> i = <span style="color: #800080;">1</span> ; i <= n; i++<span style="color: #000000;"> )
        {
            cin</span>>><span style="color: #000000;">a[i];
            p[a[i]]</span>++<span style="color: #000000;">;
            b[a[i]][p[a[i]]] </span>=<span style="color: #000000;"> i;
        }
        now </span>= <span style="color: #800080;">0</span><span style="color: #000000;">;
        </span><span style="color: #0000ff;">for</span> ( <span style="color: #0000ff;">int</span> i = <span style="color: #800080;">1</span> ; i <= n ; i++<span style="color: #000000;"> )
        {
            </span><span style="color: #0000ff;">if</span> (b[now][p[now]]==<span style="color: #800080;">0</span><span style="color: #000000;">)
            {
                cout</span><<<span style="color: #800000;">"</span><span style="color: #800000;">Impossible</span><span style="color: #800000;">"</span><<<span style="color: #000000;">endl;
                </span><span style="color: #0000ff;">return</span> <span style="color: #800080;">0</span><span style="color: #000000;">;
            }
    
            ans[i]</span>=b[now][p[now]--<span style="color: #000000;">];
            now</span>++<span style="color: #000000;">;
            </span><span style="color: #0000ff;">while</span>(now>=<span style="color: #800080;">3</span>&&p;[now]==<span style="color: #800080;">0</span><span style="color: #000000;">)
            {
                now </span>= now - <span style="color: #800080;">3</span><span style="color: #000000;">;
            }
              
    
        }
        cout</span><<<span style="color: #800000;">"</span><span style="color: #800000;">Possible</span><span style="color: #800000;">"</span><<<span style="color: #000000;">endl;
        </span><span style="color: #0000ff;">for</span> ( <span style="color: #0000ff;">int</span> i = <span style="color: #800080;">1</span>; i<=n;i++<span style="color: #000000;"> )
            cout</span><<ans[i]<<<span style="color: #800000;">"</span> <span style="color: #800000;">"</span><span style="color: #000000;">;
    
    
        </span><span style="color: #0000ff;">return</span> <span style="color: #800080;">0</span><span style="color: #000000;">;
    }</span>





















