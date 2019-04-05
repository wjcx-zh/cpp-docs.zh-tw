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
- m_nType
- ATL::CEnumeratorAccessor::m_szDescription
- CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szDescription
- ATL.CEnumeratorAccessor.m_szDescription
- CEnumeratorAccessor::m_szName
- ATL.CEnumeratorAccessor.m_szName
- m_szName
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
ms.openlocfilehash: e609b346bb4a0c2469c24e20540c646fa869ae26
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/05/2019
ms.locfileid: "59025159"
---
# <a name="cenumeratoraccessor-class"></a>CEnumeratorAccessor 類別

供[CEnumerator](../../data/oledb/cenumerator-class.md)從列舉值的資料列集存取資料。

## <a name="syntax"></a>語法

```cpp
class CEnumeratorAccessor
```

## <a name="requirements"></a>需求

**標題:** atldbcli.h

## <a name="members"></a>成員

### <a name="data-members"></a>資料成員

|||
|-|-|
|[m_bIsParent](#bisparent)|變數，指出是否列舉值的父列舉值，如果資料列的列舉值。|
|[m_nType](#ntype)|變數，表示資料列描述資料來源] 或 [列舉值。|
|[m_szDescription](#szdescription)|列舉值之資料來源的描述。|
|[m_szName](#szname)|列舉值之資料來源的名稱。|
|[m_szParseName](#szparsename)|要傳遞至字串[IParseDisplayName](/windows/desktop/api/oleidl/nn-oleidl-iparsedisplayname)來取得 moniker，針對資料來源或列舉值。|

## <a name="remarks"></a>備註

此資料列集是由資料來源並顯示從目前的列舉值的列舉值所組成。

## <a name="bisparent"></a> CEnumeratorAccessor::m_bIsParent

變數，指出是否列舉值的父列舉值，如果資料列的列舉值。

### <a name="syntax"></a>語法

```cpp
VARIANT_BOOL m_bIsParent;
```

### <a name="remarks"></a>備註

請參閱[isourcesrowset:: Getsourcesrowset](/previous-versions/windows/desktop/ms711200(v=vs.85))中*OLE DB 程式設計人員參考*如需詳細資訊。

## <a name="ntype"></a> CEnumeratorAccessor::m_nType

變數，表示資料列描述資料來源] 或 [列舉值。

### <a name="syntax"></a>語法

```cpp
USHORT m_nType;
```

### <a name="remarks"></a>備註

請參閱[isourcesrowset:: Getsourcesrowset](/previous-versions/windows/desktop/ms711200(v=vs.85))中*OLE DB 程式設計人員參考*如需詳細資訊。

## <a name="szdescription"></a> CEnumeratorAccessor::m_szDescription

列舉值之資料來源的描述。

### <a name="syntax"></a>語法

```cpp
WCHAR m_szDescription[129];
```

### <a name="remarks"></a>備註

請參閱[isourcesrowset:: Getsourcesrowset](/previous-versions/windows/desktop/ms711200(v=vs.85))中*OLE DB 程式設計人員參考*如需詳細資訊。

## <a name="szname"></a> CEnumeratorAccessor::m_szName

列舉值之資料來源的名稱。

### <a name="syntax"></a>語法

```cpp
WCHAR m_szName[129];
```

### <a name="remarks"></a>備註

請參閱[isourcesrowset:: Getsourcesrowset](/previous-versions/windows/desktop/ms711200(v=vs.85))中*OLE DB 程式設計人員參考*如需詳細資訊。

## <a name="szparsename"></a> CEnumeratorAccessor::m_szParseName

要傳遞至字串[IParseDisplayName](/windows/desktop/api/oleidl/nn-oleidl-iparsedisplayname)來取得 moniker，針對資料來源或列舉值。

### <a name="syntax"></a>語法

```cpp
WCHAR m_szParseName[129];
```

### <a name="remarks"></a>備註

請參閱[isourcesrowset:: Getsourcesrowset](/previous-versions/windows/desktop/ms711200(v=vs.85))中*OLE DB 程式設計人員參考*如需詳細資訊。

## <a name="see-also"></a>另請參閱

[OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[OLE DB 消費者樣板參考](../../data/oledb/ole-db-consumer-templates-reference.md)