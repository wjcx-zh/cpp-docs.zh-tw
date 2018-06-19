---
title: _com_error::ErrorMessage |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_error::ErrorMessage
dev_langs:
- C++
helpviewer_keywords:
- ErrorMessage method [C++]
ms.assetid: e47335b6-01af-4975-a841-121597479eb7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c16b8bb6859cd65b534d804764257b901050995b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32411228"
---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage
**Microsoft 特定的**  
  
 擷取儲存在 `HRESULT` 物件中之 `_com_error` 的字串訊息。  
  
## <a name="syntax"></a>語法  
  
```  
  
const TCHAR * ErrorMessage( ) const throw( );  
  
```  
  
## <a name="return-value"></a>傳回值  
 傳回記錄在 `HRESULT` 物件中之 `_com_error` 的字串訊息。 如果`HRESULT`是對應的 16 位元[wCode](../cpp/com-error-wcode.md)，然後一般訊息 「`IDispatch error #<wCode>`"會傳回。 如果找不到訊息，則會傳回一般訊息「`Unknown error #<hresult>`」。 傳回的字串是 Unicode 或多位元組字串，根據的狀態 **_UNICODE**巨集。  
  
## <a name="remarks"></a>備註  
 擷取記錄在 `HRESULT` 物件中之 `_com_error` 的適當系統訊息文字。 系統訊息文字透過呼叫 Win32 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351)函式。 傳回的字串會由 `FormatMessage` API 配置，並且在終結 `_com_error` 物件時釋放。  
  
 **結束 Microsoft 特定的**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)