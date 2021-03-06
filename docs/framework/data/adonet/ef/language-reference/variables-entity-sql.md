---
title: "変数 (Entity SQL) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-ado"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "ESQL"
ms.assetid: 3eed222a-f8f6-46b6-9cd5-220cc0e4e5d8
caps.latest.revision: 2
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 2
---
# 変数 (Entity SQL)
## 変数  
 変数式は、現在のスコープで定義されている名前付きの式への参照です。  変数参照は、[識別子](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md) で定義された有効な [!INCLUDE[esql](../../../../../../includes/esql-md.md)] 識別子である必要があります。  
  
 次の例は、式における変数の使用方法を示しています。  FROM 句の `c` は変数の定義です。  SELECT 句内で使用された `c` は、変数参照を表します。  
  
```  
select c   
from LOB.customers as c  
```  
  
## 参照  
 [識別子](../../../../../../docs/framework/data/adonet/ef/language-reference/identifiers-entity-sql.md)   
 [パラメーター](../../../../../../docs/framework/data/adonet/ef/language-reference/parameters-entity-sql.md)   
 [Entity SQL の概要](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)