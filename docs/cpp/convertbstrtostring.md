---
title: "ConvertBSTRToString |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- ConvertBSTRToString
dev_langs:
- C++
helpviewer_keywords:
- ConvertBSTRToString function
ms.assetid: ab6ce555-3d75-4e9c-9cb8-ada6d8ce43b1
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: c559509083d21ff8b742ef80a55ac161bbca2f53
ms.contentlocale: zh-tw
ms.lasthandoff: 09/25/2017

---
# <a name="convertbstrtostring"></a>ConvertBSTRToString
**Microsoft 特定的**  
  
 將轉換`BSTR`值設定為**char \* **。  
  
## <a name="syntax"></a>語法  
  
```  
  
      char* __stdcall ConvertBSTRToString(  
   BSTR pSrc  
);  
```  
  
#### <a name="parameters"></a>參數  
 `pSrc`  
 BSTR 變數。  
  
## <a name="remarks"></a>備註  
 `ConvertBSTRToString` 會配置您必須刪除的字串。  
  
## <a name="example"></a>範例  
  
```  
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
  
**END Microsoft 特定的**  
  
## <a name="requirements"></a>需求  
 **標頭：** comutil.h。  
  
 **Lib:** comsuppw.lib 或 comsuppwd.lib (請參閱[/zc: wchar_t （wchar_t 是原生類型）](../build/reference/zc-wchar-t-wchar-t-is-native-type.md)如需詳細資訊)  
  
## <a name="see-also"></a>另請參閱  
 [編譯器 COM 全域函式](../cpp/compiler-com-global-functions.md)
