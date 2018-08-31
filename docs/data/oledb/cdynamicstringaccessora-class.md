---
title: CDynamicStringAccessorA 類別 |Microsoft Docs
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
ms.openlocfilehash: 612050c74cf33d128f108962fab54ef6c0e8e5d9
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/29/2018
ms.locfileid: "43214561"
---
# <a name="cdynamicstringaccessora-class"></a>CDynamicStringAccessorA 類別

可讓您存取資料來源，當您有不了解資料庫結構描述 （基礎結構）。

## <a name="syntax"></a>語法

```cpp
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;
```

## <a name="remarks"></a>備註

兩者都要求提供者擷取所有的資料存取資料存放區做為字串資料，但`CDynamicStringAccessor`要求 ANSI 字串資料。

`CDynamicStringAccessorA` 繼承`GetString`並`SetString`從`CDynamicStringAccessor`。 當您使用中的這些方法時`CDynamicStringAccessorA`物件，`BaseType`是**CHAR**。

## <a name="requirements"></a>需求

**標頭檔**：atldbcli.h

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor 類別](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor 類別](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor 類別](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor 類別](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor 類別](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
