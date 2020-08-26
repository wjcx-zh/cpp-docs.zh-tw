---
title: _com_error 類別
ms.date: 11/04/2016
f1_keywords:
- _com_error
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
ms.openlocfilehash: ace3ac33e4dccd66c0a44095533d657e32b15f1c
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/25/2020
ms.locfileid: "88837810"
---
# <a name="_com_error-class"></a>_com_error 類別

**Microsoft 特定的**

**_Com_error**物件代表由類型程式庫或其中一個 com 支援類別所產生的標頭檔中，錯誤處理包裝函式所偵測到的例外狀況條件。 **_Com_error**類別會封裝 HRESULT 錯誤碼和任何相關聯的 `IErrorInfo Interface` 物件。

### <a name="construction"></a>營造

| 名稱 | 描述 |
|-|-|
|[_com_error](../cpp/com-error-com-error.md)|結構 **_com_error** 物件。|

### <a name="operators"></a>運算子

| 名稱 | 描述 |
|-|-|
|[運算子 =](../cpp/com-error-operator-equal.md)|將現有的 **_com_error** 物件指派給另一個物件。|

### <a name="extractor-functions"></a>解壓縮函數

| 名稱 | 描述 |
|-|-|
|[錯誤](../cpp/com-error-error.md)|抓取傳遞給函式的 HRESULT。|
|[ErrorInfo](../cpp/com-error-errorinfo.md)|抓取傳遞給函式的 `IErrorInfo` 物件。|
|[WCode](../cpp/com-error-wcode.md)|抓取對應至封裝 HRESULT 的16位錯誤碼。|

### <a name="ierrorinfo-functions"></a>IErrorInfo 函式

| 名稱 | 描述 |
|-|-|
|[說明](../cpp/com-error-description.md)|呼叫 `IErrorInfo::GetDescription` 函數。|
|[HelpCoNtext](../cpp/com-error-helpcontext.md)|呼叫 `IErrorInfo::GetHelpContext` 函數。|
|[HelpFile](../cpp/com-error-helpfile.md)|呼叫 `IErrorInfo::GetHelpFile` 函式|
|[Source](../cpp/com-error-source.md)|呼叫 `IErrorInfo::GetSource` 函數。|
|[GUID](../cpp/com-error-guid.md)|呼叫 `IErrorInfo::GetGUID` 函數。|

### <a name="format-message-extractor"></a>格式化訊息解壓縮

| 名稱 | 描述 |
|-|-|
|[ErrorMessage](../cpp/com-error-errormessage.md)|抓取儲存在 **_com_error** 物件中之 HRESULT 的字串訊息。|

### <a name="exepinfowcode-to-hresult-mappers"></a>ExepInfo. wCode 至 HRESULT 對應程式數目

| 名稱 | 描述 |
|-|-|
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|將32位 HRESULT 對應至16位 `wCode` 。|
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|將16位對應 `wCode` 至32位 HRESULT。|

**結束 Microsoft 專有**

## <a name="requirements"></a>規格需求

**標頭：**\<comdef.h>

`Lib:`如需詳細資訊，comsuppw .lib 或 comsuppwd.lib (參閱[/zc： wchar_t (Wchar_t 是原生類型) ](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)

## <a name="see-also"></a>另請參閱

[編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)<br/>
[IErrorInfo 介面](/windows/win32/api/oaidl/nn-oaidl-ierrorinfo)
