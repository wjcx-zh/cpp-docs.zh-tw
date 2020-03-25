---
title: _com_error 類別
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 0c33791fbe6011a3eddc6e535a3a4ed838e5e06c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80180806"
---
# <a name="_com_error-class"></a>_com_error 類別

**Microsoft 專屬**

**_Com_error**物件，代表由類型程式庫或其中一個 com 支援類別所產生之標頭檔中的錯誤處理包裝函式所偵測到的例外狀況條件。 **_Com_error**類別會封裝 HRESULT 錯誤碼和任何相關聯的 `IErrorInfo Interface` 物件。

### <a name="construction"></a>建築業

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|結構 **_com_error**物件。|

### <a name="operators"></a>操作員

|||
|-|-|
|[operator =](../cpp/com-error-operator-equal.md)|將現有的 **_com_error**物件指派給另一個。|

### <a name="extractor-functions"></a>提取函式

|||
|-|-|
|[錯誤](../cpp/com-error-error.md)|抓取傳遞至此函數的 HRESULT。|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|抓取傳遞至此函式的 `IErrorInfo` 物件。|
|[WCode](../cpp/com-error-wcode.md)|抓取對應至封裝 HRESULT 的16位錯誤碼。|

### <a name="ierrorinfo-functions"></a>IErrorInfo 函式

|||
|-|-|
|[說明](../cpp/com-error-description.md)|呼叫 `IErrorInfo::GetDescription` 函式。|
|[HelpCoNtext](../cpp/com-error-helpcontext.md)|呼叫 `IErrorInfo::GetHelpContext` 函式。|
|[説明](../cpp/com-error-helpfile.md)|呼叫 `IErrorInfo::GetHelpFile` 函式|
|[Source](../cpp/com-error-source.md)|呼叫 `IErrorInfo::GetSource` 函式。|
|[GUID](../cpp/com-error-guid.md)|呼叫 `IErrorInfo::GetGUID` 函式。|

### <a name="format-message-extractor"></a>設定訊息解壓縮的格式

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|抓取儲存在 **_com_error**物件中之 HRESULT 的字串訊息。|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo. wCode to HRESULT 對應程式

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|將 32-bit HRESULT 對應至16位 `wCode`。|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|將16位 `wCode` 對應到32位 HRESULT。|

**END Microsoft 特定的**

## <a name="requirements"></a>需求

**標頭：** \<comdef.h. h >

`Lib:` comsuppw.lib 或 comsuppwd.lib （請參閱[/zc： wchar_t （Wchar_t 是原生類型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)以取得詳細資訊）

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo 介面](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)
