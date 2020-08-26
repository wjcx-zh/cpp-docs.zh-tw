---
title: ICommandTextImpl 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- ICommandText class
- GetCommandText method
- m_strCommandText
- SetCommandText method
ms.assetid: 9c2715cc-1e55-4468-8327-85341617ed46
ms.openlocfilehash: 8d435cd8c5c8723d008be98482631f081c967058
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88845116"
---
# <a name="icommandtextimpl-class"></a>ICommandTextImpl 類別

提供 [ICommandText](/previous-versions/windows/desktop/ms714914(v=vs.85)) 介面的實作為。

## <a name="syntax"></a>語法

```cpp
template <class T >
class ATL_NO_VTABLE ICommandTextImpl
   : public ICommandImpl<T, ICommandText>
```

### <a name="parameters"></a>參數

*T*<br/>
衍生自的命令類別 `ICommandTextImpl` 。

## <a name="requirements"></a>規格需求

**標頭：** altdb。h

## <a name="members"></a>成員

### <a name="interface-methods"></a>介面方法

| 名稱 | 描述 |
|-|-|
|[GetCommandText](#getcommandtext)|傳回最後一次呼叫 [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)所設定的文字命令。|
|[SetCommandText](#setcommandtext)|設定命令文字，取代現有的命令文字。|

### <a name="data-members"></a>資料成員

| 名稱 | 描述 |
|-|-|
|[m_strCommandText](#strcommandtext)|儲存命令文字。|

## <a name="remarks"></a>備註

命令上的強制介面。

## <a name="icommandtextimplgetcommandtext"></a><a name="getcommandtext"></a> ICommandTextImpl：： GetCommandText

傳回最後一次呼叫 [SetCommandText](../../data/oledb/icommandtextimpl-setcommandtext.md)所設定的文字命令。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(GetCommandText)(GUID * pguidDialect,
   LPOLESTR * ppwszCommand);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ICommandText：： GetCommandText](/previous-versions/windows/desktop/ms709825(v=vs.85)) 。 預設會忽略 *pguidDialect* 參數。

## <a name="icommandtextimplsetcommandtext"></a><a name="setcommandtext"></a> ICommandTextImpl：： SetCommandText

設定命令文字，取代現有的命令文字。

### <a name="syntax"></a>語法

```cpp
STDMETHOD(SetCommandText)(REFGUID rguidDialect,
   LPCOLESTR pwszCommand);
```

#### <a name="parameters"></a>參數

請參閱 OLE DB 程式設計*人員參考*中的[ICommandText：： SetCommandText](/previous-versions/windows/desktop/ms709757(v=vs.85)) 。

## <a name="icommandtextimplm_strcommandtext"></a><a name="strcommandtext"></a> ICommandTextImpl：： m_strCommandText

儲存命令文字字串。

### <a name="syntax"></a>語法

```cpp
CComBSTR m_strCommandText;
```

## <a name="see-also"></a>另請參閱

[OLE DB 提供者範本](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[OLE DB 提供者範本架構](../../data/oledb/ole-db-provider-template-architecture.md)
