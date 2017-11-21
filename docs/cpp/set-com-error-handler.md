---
title: "_set_com_error_handler |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs: C++
helpviewer_keywords: _set_com_error_handler function
ms.assetid: 49fe4fca-5e37-4d83-abaf-15be5ce37f94
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 52258c64c98651fc7a962c2a246fe8bde79d8ab8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="setcomerrorhandler"></a>_set_com_error_handler
**Microsoft 特定的**  
  
 取代 COM 錯誤處理所使用的預設函式。  
  
## <a name="syntax"></a>語法  
  
```  
void __stdcall _set_com_error_handler(  
   void (__stdcall *pHandler)(  
      HRESULT hr,   
      IErrorInfo* perrinfo  
   )  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pHandler`  
 取代函式的指標。  
  
 `hr`  
 `HRESULT` 資訊。  
  
 `perrinfo`  
 `IErrorInfo` 物件  
  
## <a name="remarks"></a>備註  
 根據預設， [_com_raise_error](../cpp/com-raise-error.md)處理所有 COM 錯誤。 您可以使用 `_set_com_error_handler` 呼叫您自己的錯誤處理函式來變更這個行為。  
  
 取代函式擁有的簽章必須相當於 `_com_raise_error` 的簽章。  
  
## <a name="example"></a>範例  
  
```  
// _set_com_error_handler.cpp  
// compile with /EHsc  
#include <stdio.h>  
#include <comdef.h>  
#include <comutil.h>  
  
// Importing ado dll to attempt to establish an ado connection.  
// Not related to _set_com_error_handler   
#import "C:\Program Files\Common Files\System\ado\msado15.dll" no_namespace rename("EOF", "adoEOF")  
  
void __stdcall _My_com_raise_error(HRESULT hr, IErrorInfo* perrinfo)  
{  
   throw "Unable to establish the connection!";  
}  
  
int main()  
{  
   _set_com_error_handler(_My_com_raise_error);  
   _bstr_t bstrEmpty(L"");  
   _ConnectionPtr Connection = NULL;  
   try  
   {  
      Connection.CreateInstance(__uuidof(Connection));  
      Connection->Open(bstrEmpty, bstrEmpty, bstrEmpty, 0);   
   }  
   catch(char* errorMessage)  
   {  
      printf("Exception raised: %s\n", errorMessage);  
   }  
  
   return 0;  
}  
```  
  
```Output  
Exception raised: Unable to establish the connection!  
```  
  
## <a name="requirements"></a>需求  
 **標頭：** comdef.h  
  
 **Lib:**如果**wchar_t 是原生類型**編譯器選項已開啟，請使用 comsuppw.lib 或 comsuppwd.lib。 如果**wchar_t 是原生類型**已關閉，請使用 comsupp.lib。 如需詳細資訊，請參閱 [/Zc:wchar_t (wchar_t 是原生類型)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)。  
  
## <a name="see-also"></a>另請參閱  
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)