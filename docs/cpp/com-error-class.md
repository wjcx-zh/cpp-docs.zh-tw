---
title: "_com_error 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- _com_error
dev_langs:
- C++
helpviewer_keywords:
- _com_error class
ms.assetid: 70dafa69-b1fb-4a5c-9249-e857e0793d42
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 670be1988adb3ef5afa9113b9988ceafb249801f
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="comerror-class"></a>_com_error 類別
**Microsoft 特定的**  
  
 A`_com_error`物件表示偵測到的錯誤處理包裝函式中產生類型程式庫的標頭檔或其中一個 COM 支援類別的例外狀況。 `_com_error`類別會封裝`HRESULT`錯誤程式碼和所有相關聯`IErrorInfo Interface`物件。  
  
### <a name="construction"></a>建構  
  
|||  
|-|-|  
|[_com_error](../cpp/com-error-com-error.md)|建構 `_com_error` 物件。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 =](../cpp/com-error-operator-equal.md)|將現有的 `_com_error` 物件指派給另一個物件。|  
  
### <a name="extractor-functions"></a>擷取程式函式  
  
|||  
|-|-|  
|[錯誤](../cpp/com-error-error.md)|擷取傳遞給建構函式的 `HRESULT`。|  
|[ErrorInfo](../cpp/com-error-errorinfo.md)|擷取`IErrorInfo`物件傳遞至建構函式。|  
|[WCode](../cpp/com-error-wcode.md)|擷取對應至封裝的 `HRESULT` 的 16 位元錯誤碼。|  
  
### <a name="ierrorinfo-functions"></a>IErrorInfo 函式  
  
|||  
|-|-|  
|[說明](../cpp/com-error-description.md)|呼叫`IErrorInfo::GetDescription`函式。|  
|[HelpContext](../cpp/com-error-helpcontext.md)|呼叫`IErrorInfo::GetHelpContext`函式。|  
|[說明檔](../cpp/com-error-helpfile.md)|呼叫`IErrorInfo::GetHelpFile`函式|  
|[Source](../cpp/com-error-source.md)|呼叫`IErrorInfo::GetSource`函式。|  
|[GUID](../cpp/com-error-guid.md)|呼叫`IErrorInfo::GetGUID`函式。|  
  
### <a name="format-message-extractor"></a>格式訊息擷取程式  
  
|||  
|-|-|  
|[錯誤訊息](../cpp/com-error-errormessage.md)|擷取字串訊息的 HRESULT 會儲存在`_com_error`物件。|  
  
### <a name="exepinfowcode-to-hresult-mappers"></a>以 HRESULT 自行 ExepInfo.wCode  
  
|||  
|-|-|  
|[HRESULTToWCode](../cpp/com-error-hresulttowcode.md)|32 位元會對應`HRESULT`至 16 位元`wCode`。|  
|[WCodeToHRESULT](../cpp/com-error-wcodetohresult.md)|將 16 位元的 `wCode` 對應至 32 位元的 `HRESULT`。|  
  
**END Microsoft 特定的**  
  
## <a name="requirements"></a>需求  
 **標頭：** comdef.h  
  
 `Lib:`comsuppw.lib 或 comsuppwd.lib (請參閱[/zc: wchar_t （wchar_t 是原生類型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)如需詳細資訊)  
  
## <a name="see-also"></a>另請參閱  
 [編譯器 COM 支援類別](../cpp/compiler-com-support-classes.md)   
 [IErrorInfo 介面](http://msdn.microsoft.com/en-us/4dda6909-2d9a-4727-ae0c-b5f90dcfa447)
