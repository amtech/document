# 数据仓库架构

企业数据仓库（数据中心）对ETL抽取而来的业务数据进行分层存储。分层架构分为： SRC层、ODS层、数据集市层（DM），形成了睿思科技BI系统分层数据架构。

SRC层

SRC层存放原始数据，ETL从其他业务系统抽取的数据在经过清洗和预处理后首先放入SRC层。

ODS层

ODS层是一个面向数据主题的、集成的、可变的、当前的细节数据集合层，用于支持企业对于即时性的、操作性的、集成的全体信息的需求。常常被作为数据仓库的数据处理的过渡，以降低直接进行数据处理的复杂度。

数据集市（DM）

数据集市作为商业智能系统的组成部分，从企业数据仓库中ODS层、抽取相关数据并进行转换和装载，并根据应用需求形成的数据集合，支撑各个业务部门及人员进行建设专业化应用。
