---
title: ICommandTextImpl 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ICommandText
- GetCommandText
- ICommandTextImpl.GetCommandText
- ICommandTextImpl::GetCommandText
- ATL::ICommandTextImpl::m_strCommandText
- ICommandTextImpl<T>::m_strCommandText
- m_strCommandText
- ICommandTextImpl.m_strCommandText
- ICommandTextImpl::m_strCommandText
- ATL::ICommandTextImpl<T>::m_strCommandText
- ATL.ICommandTextImpl.m_strCommandText
- ICommandTextImpl.SetCommandText
- ICommandTextImpl::SetCommandText
- SetCommandText
dev_langs:
- C++
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e190f81c0097e707830f7ac09c801929ea3e85e9
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572543"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl 類別
提供實作[ICommandText](/previous-versions/windows/desktop/ms714914\(v=vs.85\))介面。  
  
## <a name="syntax"></a>語法

```cpp
template <class T >  
class ATL_NO_VTABLE ICommandTextImpl   
   : public ICommandImpl<T, ICommandText>  
```  
  
### <a name="parameters"></a>參數  
 *T*  
 命令類別衍生自`ICommandTextImpl`。 

## <a name="requirements"></a>需求  
 **標頭：** altdb.h  
  
## <a name="members"></a>成員  
  
### <a name="interface-methods"></a>介面方法  
  
|||  
|-|-|  
|[GetCommandText](#getcommandtext)|傳回上次呼叫所設定的文字命令[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)。|  
|[SetCommandText](#setcommandtext)|設定命令文字，取代現有的命令文字。|  
  
### <a name="data-members"></a>資料成員  
  
|||  
|-|-|  
|[m_strCommandText](#strcommandtext)|儲存命令文字。|  
  
## <a name="remarks"></a>備註  
 在命令中的強制介面。  
 
## <a name="getcommandtext"></a> Icommandtextimpl:: Getcommandtext
傳回上次呼叫所設定的文字命令[SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,   
   LPOLESTR * ppwszCommand);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[ICommandText::GetCommandText](/previous-versions/windows/desktop/ms709825\(v=vs.85\))中*OLE DB 程式設計人員參考*。 *PguidDialect*依預設，會忽略參數。  

## <a name="setcommandtext"></a> Icommandtextimpl:: Setcommandtext
設定命令文字，取代現有的命令文字。  
  
### <a name="syntax"></a>語法  
  
```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,   
   LPCOLESTR pwszCommand);  
```  
  
#### <a name="parameters"></a>參數  
 請參閱[icommandtext:: Setcommandtext](/previous-versions/windows/desktop/ms709757\(v=vs.85\))中*OLE DB 程式設計人員參考*。 

## <a name="strcommandtext"></a> Icommandtextimpl:: M_strcommandtext
儲存命令的文字字串。  
  
### <a name="syntax"></a>語法  
  
```cpp
CComBSTR m_strCommandText;  
```  
  
## <a name="see-also"></a>另請參閱  
 [OLE DB 提供者樣板](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)