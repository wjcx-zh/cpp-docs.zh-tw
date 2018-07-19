---
title: ConvertBSTRToString |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- ConvertBSTRToString
dev_langs:
- C++
helpviewer_keywords:
- ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1278ab84ea8888b34290c9738e0eb88a4485e99c
ms.sourcegitcommit: 1fd1eb11f65f2999dfd93a2d924390ed0a0901ed
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2018
ms.locfileid: "37942839"
---
# <a name="convertbstrtostring"></a>ConvertBSTRToString
**Microsoft 專屬**  
  
 將轉換`BSTR`值加入**char \*** 。  
  
## <a name="syntax"></a>語法  
  
```  
  
char* __stdcall ConvertBSTRToString(BSTR pSrc);  
```  
  
#### <a name="parameters"></a>參數  
 *pSrc*  
 BSTR 變數。  
  
## <a name="remarks"></a>備註  
 `ConvertBSTRToString` 會配置您必須刪除的字串。  
  
## <a name="example"></a>範例  
  
```cpp 
// ConvertBSTRToString.cpp  
#include <comutil.h>  
#include <stdio.h>  
  
#pragma comment(lib, "comsuppw.lib")  
  
int main() {  
   BSTR bstrText = ::SysAllocString(L"Test");  
   wprintf_s(L"BSTR text: %s\n", bstrText);  
  
   char* lpszText2 = _com_util::ConvertBSTRToString(bstrText);  
   printf_s("char * text: %s\n", lpszText2);  
  
   SysFreeString(bstrText);  
   delete[] lpszText2;  
}  
```  
  
```Output  
BSTR text: Test  
char * text: Test  
```  
  
**結束 Microsoft 專屬**  
  
## <a name="requirements"></a>需求  
 **標頭：** \<comutil.h >。  
  
 **Lib:** comsuppw.lib 或 comsuppwd.lib (請參閱 < [/zc: wchar_t （wchar_t 是原生型別）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)如需詳細資訊)  
  
## <a name="see-also"></a>另請參閱  
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)