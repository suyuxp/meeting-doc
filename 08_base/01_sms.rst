消息通知
================


.. graphviz::
   
   digraph idp_modules{
     fontname = "Microsoft YaHei";
     rankdir = TB;
     fontsize = 12;
     
     node [fontname = "Microsoft YaHei", fontsize = 12, shape = "record" ];
     edge [fontname = "Microsoft YaHei", fontsize = 12 ];
     
         subgraph cluster_sl{
             label=" IDP支持层";
             bgcolor="mintcream";
             node [shape="Mrecord", color="skyblue", style="filled"];
             network_mgr [label=" 网络管理器"];
             log_mgr [label=" 日志管理器"];
             module_mgr [label=" 模块管理器"];
             conf_mgr [label=" 配置管理器"];
             db_mgr [label=" 数据库管理器"];
         };
     
         subgraph cluster_md{
             label=" 可插拔模块集";
             bgcolor="lightcyan";
             node [color="chartreuse2", style="filled"];
             mod_dev [label=" 开发支持模块"];
             mod_dm [label=" 数据建模模块"];
             mod_dp [label=" 部署发布模块"];
         };
     
     mod_dp -> mod_dev [label="依赖..."];
     mod_dp -> mod_dm [label="依赖..."];
     mod_dp -> module_mgr [label="安装...", color="yellowgreen", arrowhead="none"];
     mod_dev -> mod_dm [label="依赖..."];
     mod_dev -> module_mgr [label="安装...", color="yellowgreen", arrowhead="none"];
     mod_dm -> module_mgr [label="安装...", color="yellowgreen", arrowhead="none"];
   }



.. graphviz::

	digraph G {
	    rankdir="LR";
	    node[shape="point", width=0, height=0];
	    edge[arrowhead="none", style="dashed"]

	    {
	        rank="same";
	        edge[style="solided"];
	        LC[shape="plaintext"];
	        LC -> step00 -> step01 -> step02 -> step03 -> step04 -> step05;
	    }

	    {
	        rank="same";
	        edge[style="solided"];
	        Agency[shape="plaintext"];
	        Agency -> step10 -> step11 -> step12 -> step13 -> step14 -> step15;
	    }

	    {
	        rank="same";
	        edge[style="solided"];
	        Agent[shape="plaintext"];
	        Agent -> step20 -> step21 -> step22 -> step23 -> step24 -> step25;
	    }

	    step00 -> step10 [label="sends email new custumer", arrowhead="normal"];
	    step11 -> step01 [label="declines", arrowhead="normal"];
	    step12 -> step02 [label="accepts", arrowhead="normal"];
	    step13 -> step23 [label="forward to", arrowhead="normal"];
	    step24 -> step14;
	    step14 -> step04 [arrowhead="normal"];
	}