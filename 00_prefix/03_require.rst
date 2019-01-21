系统核心功能设计
========================


主流程
------------------------

.. graphviz::

    digraph flow {
        margin = 0.5;
        bgcolor = "transparent";
        rankdir = "LR";

        node [shape="box"];

        {
            rank = "same";
            b1 [label="筹备会议"];
            b2 [label="报名设置"];
            b3 [label="启动报名"];
            b4 [label="关闭报名"];
            b1 -> b2 -> b3 -> b4;
        }

        {
            rank = "same";
            c1 [label="线上报名\n团队报名"];
            c2 [label="审核"];
            c3 [label="缴费"];
            c4 [label="标签分组"];
            c1 -> c2 -> c3 -> c4;
        }


        {
            rank = "same";
            d1 [label="酒店入住"];
            d2 [label="签到"];
            d3 [label="考勤"];
            d1 -> d2 -> d3;
        }

        b3 -> c1;
        c3 -> d1;
        c4 -> d2;
    }


核心功能
-----------------------

#. :ref:`startup`