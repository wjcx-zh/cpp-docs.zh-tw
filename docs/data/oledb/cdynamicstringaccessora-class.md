---
title: CDynamicStringAccessorA 類別 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CDynamicStringAccessorA
dev_langs:
- C++
helpviewer_keywords:
- CDynamicStringAccessorA class
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d6d05ac97846f55cf65d4010179b28d2b543ef66
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicstringaccessora-class"></a>CDynamicStringAccessorA 類別
可讓您存取資料來源，當您在不知道資料庫結構描述 （基礎結構）。  
  
## <a name="syntax"></a>語法

```cpp
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;  
```  
  
## <a name="remarks"></a>備註  
 它們都要求提供者擷取從資料存放區做為字串資料存取的所有資料，但`CDynamicStringAccessor`要求 ANSI 字串資料。  
  
 `CDynamicStringAccessorA` 繼承**GetString**和`SetString`從`CDynamicStringAccessor`。 當您使用這些方法進行`CDynamicStringAccessorA`物件***BaseType***是**CHAR**。  
  
## <a name="requirements"></a>需求  
 **標頭檔**：atldbcli.h  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)   
 [CAccessor 類別](../../data/oledb/caccessor-class.md)   
 [CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)   
 [CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)   
 [CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)   
 [CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)