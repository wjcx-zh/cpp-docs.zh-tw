---
title: _com_error 類別
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 8ed1521cbf768e5b473281e5f9b7c6597cdc4692
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51519551"
---
# <a name="comerror-class"></a>_com_error 類別

**Microsoft 專屬**

A **_com_error**物件表示偵測到的錯誤處理包裝函式產生自類型程式庫標頭檔中或其中一個 COM 支援類別的例外狀況。 **_Com_error**類別會封裝的 HRESULT 錯誤碼和任何相關聯`IErrorInfo Interface`物件。

### <a name="construction"></a>建構

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|建構 **_com_error**物件。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator =](../cpp/com-error-operator-equal.md)|指派的現有 **_com_error**到另一個物件。|

### <a name="extractor-functions"></a>擷取程式函式

|||
|-|-|
|[錯誤](../cpp/com-error-error.md)|擷取傳遞給建構函式的 HRESULT。|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|擷取`IErrorInfo`物件傳遞至建構函式。|
|[WCode](../cpp/com-error-wcode.md)|擷取 16 位元錯誤碼對應至封裝的 HRESULT。|

### <a name="ierrorinfo-functions"></a>IErrorInfo 函式

|||
|-|-|
|[描述](../cpp/com-error-description.md)|呼叫`IErrorInfo::GetDescription`函式。|
|[HelpContext](../cpp/com-error-helpcontext.md)|呼叫`IErrorInfo::GetHelpContext`函式。|
|[HelpFile](../cpp/com-error-helpfile.md)|呼叫`IErrorInfo::GetHelpFile`函式|
|[來源](../cpp/com-error-source.md)|呼叫`IErrorInfo::GetSource`函式。|
|[GUID](../cpp/com-error-guid.md)|呼叫`IErrorInfo::GetGUID`函式。|

### <a name="format-message-extractor"></a>格式訊息擷取程式

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|擷取字串訊息的 HRESULT 儲存 **_com_error**物件。|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo.wCode HRESULT 對應程式

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|對應到 16 位元的 32 位元 HRESULT `wCode`。|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|將對應的 16 位元`wCode`成 32 位元 HRESULT。|

**結束 Microsoft 專屬**

## <a name="requirements"></a>需求

**標頭：** \<comdef.h >

`Lib:` comsuppw.lib 或 comsuppwd.lib (請參閱[/zc: wchar_t （wchar_t 是原生型別）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)如需詳細資訊)

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo 介面](/windows/desktop/api/oaidl/nn-oaidl-ierrorinfo)