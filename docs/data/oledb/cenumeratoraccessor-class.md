---
title: CEnumeratorAccessor 類別
ms.date: 11/04/2016
f1_keywords:
- ATL::CEnumeratorAccessor
- CEnumeratorAccessor
- ATL.CEnumeratorAccessor
- CEnumeratorAccessor.m_bIsParent
- ATL::CEnumeratorAccessor::m_bIsParent
- m_bIsParent
- ATL.CEnumeratorAccessor.m_bIsParent
- CEnumeratorAccessor::m_bIsParent
- ATL::CEnumeratorAccessor::m_nType
- CEnumeratorAccessor.m_nType
- CEnumeratorAccessor::m_nType
- ATL.CEnumeratorAccessor.m_nType
- ATL::CEnumeratorAccessor::m_szDescription
- CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szDescription
- ATL.CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szName
- ATL.CEnumeratorAccessor.m_szName
- ATL::CEnumeratorAccessor::m_szName
- CEnumeratorAccessor.m_szName
- CEnumeratorAccessor::m_szParseName
- ATL::CEnumeratorAccessor::m_szParseName
- m_szParseName
- CEnumeratorAccessor.m_szParseName
- ATL.CEnumeratorAccessor.m_szParseName
helpviewer_keywords:
- CEnumeratorAccessor class
- m_bIsParent
- m_nType
- m_szDescription
- m_szName
- m_szParseName
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
ms.openlocfilehash: 0b4baa4671a013699e51a9ab28c002a680dfcd61
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88838135"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor 類別

供 [CEnumerator](../../data/oledb/cenumerator-class.md) 用來存取列舉值資料列集的資料。

## <a name="syntax"></a>語法

```cpp
class CEnumeratorAccessor
```

## <a name="requirements"></a>規格需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="data-members"></a>資料成員

| 名稱 | 描述 |
|-|-|
|[m_bIsParent](#bisparent)|變數，指出列舉值是否為父代列舉值（如果資料列是列舉值）。|
|[m_nType](#ntype)|變數，指出資料列是否描述資料來源或列舉值。|
|[m_szDescription](#szdescription)|資料來源或列舉值的描述。|
|[m_szName](#szname)|資料來源或列舉值的名稱。|
|[m_szParseName](#szparsename)|要傳遞至 [IParseDisplayName](/windows/win32/api/oleidl/nn-oleidl-iparsedisplayname) 以取得資料來源或列舉值之標記的字串。|

## <a name="remarks"></a>備註

此資料列集是由目前列舉值所顯示的資料來源和列舉值所組成。

## <a name="cenumeratoraccessorm_bisparent"></a><a name="bisparent"></a> CEnumeratorAccessor：： m_bIsParent

變數，指出列舉值是否為父代列舉值（如果資料列是列舉值）。

### <a name="syntax"></a>語法

```cpp
VARIANT_BOOL m_bIsParent;
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱*OLE DB 程式設計人員參考*中的[ISourcesRowset：： GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 。

## <a name="cenumeratoraccessorm_ntype"></a><a name="ntype"></a> CEnumeratorAccessor：： m_nType

變數，指出資料列是否描述資料來源或列舉值。

### <a name="syntax"></a>語法

```cpp
USHORT m_nType;
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱*OLE DB 程式設計人員參考*中的[ISourcesRowset：： GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 。

## <a name="cenumeratoraccessorm_szdescription"></a><a name="szdescription"></a> CEnumeratorAccessor：： m_szDescription

資料來源或列舉值的描述。

### <a name="syntax"></a>語法

```cpp
WCHAR m_szDescription[129];
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱*OLE DB 程式設計人員參考*中的[ISourcesRowset：： GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 。

## <a name="cenumeratoraccessorm_szname"></a><a name="szname"></a> CEnumeratorAccessor：： m_szName

資料來源或列舉值的名稱。

### <a name="syntax"></a>語法

```cpp
WCHAR m_szName[129];
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱*OLE DB 程式設計人員參考*中的[ISourcesRowset：： GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 。

## <a name="cenumeratoraccessorm_szparsename"></a><a name="szparsename"></a> CEnumeratorAccessor：： m_szParseName

要傳遞至 [IParseDisplayName](/windows/win32/api/oleidl/nn-oleidl-iparsedisplayname) 以取得資料來源或列舉值之標記的字串。

### <a name="syntax"></a>語法

```cpp
WCHAR m_szParseName[129];
```

### <a name="remarks"></a>備註

如需詳細資訊，請參閱*OLE DB 程式設計人員參考*中的[ISourcesRowset：： GetSourcesRowset](/previous-versions/windows/desktop/ms711200(v=vs.85)) 。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者範本](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 取用者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)
