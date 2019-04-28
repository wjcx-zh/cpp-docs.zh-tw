---
title: CDynamicStringAccessorW 類別
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessorW
helpviewer_keywords:
- CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
ms.openlocfilehash: 20ea4a2d795108e00c4b11c3abea6cf7b9953ca7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230784"
---
# <a name="cdynamicstringaccessorw-class"></a>CDynamicStringAccessorW 類別

可讓您存取資料來源，當您有不了解資料庫結構描述 （基礎結構）。

## <a name="syntax"></a>語法

```cpp
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;
```

## <a name="remarks"></a>備註

兩者都要求提供者擷取所有的資料存取資料存放區做為字串資料，但`CDynamicStringAccessor`要求 Unicode 字串資料。

`CDynamicStringAccessorW` 繼承`GetString`並`SetString`從`CDynamicStringAccessor`。 當您使用中的這些方法時`CDynamicStringAccessorW`物件，`BaseType`是**WCHAR**。

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
