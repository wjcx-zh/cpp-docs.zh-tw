---
title: CEnumerator 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- CEnumerator
- CEnumerator::Find
- ATL::CEnumerator::Find
- ATL.CEnumerator.Find
- CEnumerator.Find
- GetMoniker
- CEnumerator.GetMoniker
- CEnumerator::GetMoniker
- ATL.CEnumerator.GetMoniker
- ATL::CEnumerator::GetMoniker
- ATL.CEnumerator.Open
- CEnumerator::Open
- ATL::CEnumerator::Open
- CEnumerator.Open
dev_langs:
- C++
helpviewer_keywords:
- CEnumerator class
- Find method
- GetMoniker method
- Open method
ms.assetid: 25805f1b-26e3-402f-af83-1b5fe5ddebf7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 37d53932a283ea047d748985a1da348d9346ce1e
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2018
ms.locfileid: "39336962"
---
# <a name="cenumerator-class"></a>CEnumerator 類別
使用 OLE DB 列舉值物件，它會公開[ISourcesRowset](https://msdn.microsoft.com/library/ms715969.aspx)介面，以傳回描述所有的資料來源和列舉值的資料列集。  
  
## <a name="syntax"></a>語法

```cpp
class CEnumerator :   
   public CAccessorRowset< CAccessor <CEnumeratorAccessor >>  
```  

## <a name="requirements"></a>需求  
 **標頭：** atldbcli.h
  
## <a name="members"></a>成員  
  
### <a name="methods"></a>方法  
  
|||  
|-|-|  
|[尋找](#find)|可用的提供者 （資料來源） 搜尋尋找具有指定名稱的其中一個。|  
|[GetMoniker](#getmoniker)|擷取`IMoniker`目前記錄的介面。|  
|[開啟](#open)|開啟 列舉值。|  
  
## <a name="remarks"></a>備註  
 您可以擷取`ISourcesRowset`間接從這個類別的資料。  

## <a name="find"></a> Cenumerator:: Find
在可用提供者中尋找指定的名稱。  
  
### <a name="syntax"></a>語法  
  
```cpp
bool Find(TCHAR* szSearchName) throw();  
```  
  
#### <a name="parameters"></a>參數  
 *szSearchName*  
 [in] 要搜尋的名稱。  
  
### <a name="return-value"></a>傳回值  
 **true**如果找不到名稱。 否則，請**false**。  
  
### <a name="remarks"></a>備註  
 此名稱會對應到`SOURCES_NAME`隸屬[ISourcesRowset](https://msdn.microsoft.com/library/ms715969.aspx)介面。  
  
## <a name="getmoniker"></a> Cenumerator:: Getmoniker
剖析顯示名稱，以擷取元件可以轉換成 moniker 的字串。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT GetMoniker(LPMONIKER* ppMoniker) const throw();  

HRESULT GetMoniker(LPMONIKER* ppMoniker,   
   LPCTSTR lpszDisplayName) const throw();  
```  
  
#### <a name="parameters"></a>參數  
 *ppMoniker*  
 [out]Moniker 所剖析的顯示名稱 ([cenumeratoraccessor:: M_szparsename](../../data/oledb/cenumeratoraccessor-m-szparsename.md)) 之目前資料列。  
  
 *lpszDisplayName*  
 [in]要剖析的顯示名稱。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT。  

## <a name="open"></a> Cenumerator:: Open
會將繫結之 moniker 的列舉值，如果其中一個指定，則擷取資料列集列舉值，藉由呼叫[isourcesrowset:: Getsourcesrowset](https://msdn.microsoft.com/library/ms711200.aspx)。  
  
### <a name="syntax"></a>語法  
  
```cpp
HRESULT Open(LPMONIKER pMoniker) throw();  

HRESULT Open(const CLSID* pClsid = & CLSID_OLEDB_ENUMERATOR) throw();  

HRESULT Open(const CEnumerator& enumerator) throw();  
```  
  
#### <a name="parameters"></a>參數  
 *pMoniker*  
 [in]Moniker 的列舉值的指標。  
  
 *pClsid*  
 [in]指標`CLSID`列舉程式。  
  
 *enumerator*  
 [in]列舉值的參考。  
  
### <a name="return-value"></a>傳回值  
 標準的 HRESULT。  
  
## <a name="see-also"></a>另請參閱  
 [DBViewer](../../visual-cpp-samples.md)   
 [OLE DB 消費者樣板](../../data/oledb/ole-db-consumer-templates-cpp.md)   
 [OLE DB 消費者範本參考](../../data/oledb/ole-db-consumer-templates-reference.md)