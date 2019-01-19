.. _entry_group:

团队报名
===========

描述
-----------

团队报名是指机构组织学员统一申请参加会议。


现状
^^^^^^^^^^^^

目前，是由招生组将报名的电子表格发给各个机构的负责人，
机构负责人填报好电子表格后，再返回给招生组负责人，
然后再由招生组负责人导入系统。

这个过程非常的不方便，存在以下问题难以解决。

#. 报名学员的任何变更，都需要招生组负责人修订
#. 电子表格经常被填写人随意修改，造成无法导入
#. 电子表格中经常有错误的数据格式，无法及时发现
#. 对于会议特定的数据项，需要单独设置电子表格

因此，团队报名必须要重新设计。


需求
------------

主流程图
^^^^^^^^^^^^

.. graphviz::

    digraph flow {
        margin = 0.5;
        bgcolor = "transparent";
        rankdir = TB;
        size = "5,8";

        node [shape="record"];
        edge [style="dashed"];

        a [label="{开始}", style="filled", fillcolor="chartreuse", color="black"];
        b [label="{登记机构信息}"];

        {
            ranke = "same";
            c [label="{线上批量填报}"];
        }

        d [label="审核通过否?", shape="diamond"];
        f [label="{整体入库}"];
        g [label="{结束}", style="filled", fillcolor="chartreuse"];

        node [shape="point", width=0, height=0];

        a -> b [label="招生组联系机构对接人"];
        b -> c -> d;
        d -> f [label="通过"];
        f -> g;

        {
            rank = "same";
            e;
            edge [fontcolor="red", color="red", arrowhead="none"];
            d -> e [label="未通过"];
            e -> s1;
        }

        s1 -> c [color="red"];
    }



用例清单
^^^^^^^^^^^^^

#. [UC-20201] 登记报名机构信息
#. [UC-20202] 颁发机构报名授权码
#. [UC-20203] 线上批量报名
#. [UC-20204] 审核团队批名
#. [UC-20205] 增加报名学员
#. [UC-20206] 变更报名学员
#. [UC-20207] 撤销报名学员
#. [UC-20208] 增加与变更的审核


设计
------------

领域架构图
^^^^^^^^^^^^

原型设计
^^^^^^^^^^^^

