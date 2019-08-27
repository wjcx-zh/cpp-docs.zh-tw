---
title: _com_error 類別
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: 828a1ec68fef631700d5b64e6aeeec6660acf9a8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498738"
---
# <a name="_com_error-class"></a>_com_error 類別

**Microsoft 專屬**

**_Com_error**物件代表由類型程式庫或其中一個 com 支援類別所產生之標頭檔中的錯誤處理包裝函式所偵測到的例外狀況條件。 **_Com_error**類別會封裝 HRESULT 錯誤碼和任何相關聯`IErrorInfo Interface`的物件。

### <a name="construction"></a>建構

|||
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|結構 **_com_error**物件。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator =](../cpp/com-error-operator-equal.md)|將現有的 **_com_error**物件指派給另一個。|

### <a name="extractor-functions"></a>提取函式

|||
|-|-|
|[錯誤](../cpp/com-error-error.md)|抓取傳遞至此函數的 HRESULT。|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|抓取傳遞`IErrorInfo`至此函式的物件。|
|[WCode](../cpp/com-error-wcode.md)|抓取對應至封裝 HRESULT 的16位錯誤碼。|

### <a name="ierrorinfo-functions"></a>IErrorInfo 函式

|||
|-|-|
|[描述](../cpp/com-error-description.md)|呼叫`IErrorInfo::GetDescription`函式。|
|[HelpContext](../cpp/com-error-helpcontext.md)|呼叫`IErrorInfo::GetHelpContext`函式。|
|[HelpFile](../cpp/com-error-helpfile.md)|呼叫`IErrorInfo::GetHelpFile`函式|
|[Source](../cpp/com-error-source.md)|呼叫`IErrorInfo::GetSource`函式。|
|[GUID](../cpp/com-error-guid.md)|呼叫`IErrorInfo::GetGUID`函式。|

### <a name="format-message-extractor"></a>設定訊息解壓縮的格式

|||
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|抓取 **_com_error**物件中儲存之 HRESULT 的字串訊息。|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo. wCode to HRESULT 對應程式

|||
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|將 32-bit HRESULT 對應至16位`wCode`。|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|將16位`wCode`對應至32位 HRESULT。|

**結束 Microsoft 專屬**

## <a name="requirements"></a>需求

**標頭:** \<comdef.h. h >

`Lib:`comsuppw.lib .lib 或 comsuppwd.lib (請參閱[/zc: wchar_t (Wchar_t 是原生類型)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)以取得詳細資訊)

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo 介面](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)