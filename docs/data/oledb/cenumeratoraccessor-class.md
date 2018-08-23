---
title: CEnumeratorAccessor 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CEnumeratorAccessor class
- m_bIsParent
- m_nType
- m_szDescription
- m_szName
- m_szParseName
ms.assetid: 21e8e7ea-3511-4afe-b33f-d520f4ff82bb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 8eea759f7f2af32fe688bbc8583eafc1244b20d7
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42573212"
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
|[m_szParseName](#szparsename)|要傳遞至字串[IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604)來取得 moniker，針對資料來源或列舉值。|  
  
## <a name="remarks"></a>備註  
 此資料列集是由資料來源並顯示從目前的列舉值的列舉值所組成。  
  
## <a name="bisparent"></a> Cenumeratoraccessor:: M_bisparent
變數，指出是否列舉值的父列舉值，如果資料列的列舉值。  
  
### <a name="syntax"></a>語法  
  
```cpp
VARIANT_BOOL m_bIsParent;  
```  
  
### <a name="remarks"></a>備註  
 請參閱[isourcesrowset:: Getsourcesrowset](/previous-versions/windows/desktop/ms711200\(v=vs.85\))中*OLE DB 程式設計人員參考*如需詳細資訊。 

## <a name="ntype"></a> Cenumeratoraccessor:: M_ntype
變數，表示資料列描述資料來源] 或 [列舉值。  
  
### <a name="syntax"></a>語法  
  
```cpp
USHORT m_nType;  
```  
  
### <a name="remarks"></a>備註  
 請參閱[isourcesrowset:: Getsourcesrowset](/previous-versions/windows/desktop/ms711200\(v=vs.85\))中*OLE DB 程式設計人員參考*如需詳細資訊。

## <a name="szdescription"></a> Cenumeratoraccessor:: M_szdescription
列舉值之資料來源的描述。  
  
### <a name="syntax"></a>語法  
  
```cpp
WCHAR m_szDescription[129];  
```  
  
### <a name="remarks"></a>備註  
 請參閱[isourcesrowset:: Getsourcesrowset](/previous-versions/windows/desktop/ms711200\(v=vs.85\))中*OLE DB 程式設計人員參考*如需詳細資訊。

## <a name="szname"></a> Cenumeratoraccessor:: M_szname
列舉值之資料來源的名稱。  
  
### <a name="syntax"></a>語法  
  
```cpp
WCHAR m_szName[129];  
```  
  
### <a name="remarks"></a>備註  
 請參閱[isourcesrowset:: Getsourcesrowset](/previous-versions/windows/desktop/ms711200\(v=vs.85\))中*OLE DB 程式設計人員參考*如需詳細資訊。  

## <a name="szparsename"></a> Cenumeratoraccessor:: M_szparsename
要傳遞至字串[IParseDisplayName](http://msdn.microsoft.com/library/windows/desktop/ms680604)來取得 moniker，針對資料來源或列舉值。  
  
### <a name="syntax"></a>語法  
  
```cpp
WCHAR m_szParseName[129];  
```  
  
### <a name="remarks"></a>備註  
 請參閱[isourcesrowset:: Getsourcesrowset](/previous-versions/windows/desktop/ms711200\(v=vs.85\))中*OLE DB 程式設計人員參考*如需詳細資訊。  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)