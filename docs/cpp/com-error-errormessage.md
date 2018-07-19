---
title: _com_error::ErrorMessage |Microsoft Docs
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
ms.openlocfilehash: 2bff5e8f84b316f028daf503c3013667c82aaa4e
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37940562"
---
# <a name="comerrorerrormessage"></a>_com_error::ErrorMessage
**Microsoft 專屬**  
  
 擷取字串訊息的 HRESULT 儲存`_com_error`物件。  
  
## <a name="syntax"></a>語法  
  
```  
  
const TCHAR * ErrorMessage( ) const throw( );  
  
```  
  
## <a name="return-value"></a>傳回值  
 傳回字串訊息的 HRESULT 記錄`_com_error`物件。 如果 HRESULT 是對應的 16 位元[wCode](../cpp/com-error-wcode.md)，然後一般訊息 「`IDispatch error #<wCode>`"會傳回。 如果找不到訊息，則會傳回一般訊息「`Unknown error #<hresult>`」。 傳回的字串是 Unicode 或多位元組字串，根據 _UNICODE 巨集的狀態。  
  
## <a name="remarks"></a>備註  
 HRESULT 記錄內擷取適當的系統訊息文字`_com_error`物件。 系統訊息文字由呼叫 Win32 [FormatMessage](http://msdn.microsoft.com/library/windows/desktop/ms679351)函式。 傳回的字串會由 `FormatMessage` API 配置，並且在終結 `_com_error` 物件時釋放。  
  
 **結束 Microsoft 專屬**  
  
## <a name="see-also"></a>另請參閱  
 [_com_error 類別](../cpp/com-error-class.md)