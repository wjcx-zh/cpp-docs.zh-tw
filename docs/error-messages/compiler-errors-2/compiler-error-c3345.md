---
title: "編譯器錯誤 C3345 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3345
dev_langs:
- C++
helpviewer_keywords:
- C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
caps.latest.revision: 4
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: 0d9cbb01d1ad0f2ea65d59334cb88140ef18fce0
ms.openlocfilehash: 462e11e6959e7edb2bdda6081f4cabea17996e91
ms.lasthandoff: 04/12/2017

---
# <a name="compiler-error-c3345"></a>編譯器錯誤 C3345
'identifier': 模組名稱的無效識別項  
  
 模組的 *識別項* 包含一或多個無法接受的字元。 有效識別項的第一個字元必須是字母、底線或 High ANSI (0x80-FF) 字元，而且之後的任何字元必須是英數字元、底線或 High ANSI 字元。  
  
### <a name="to-correct-this-error"></a>更正這個錯誤  
  
1.  確定 *識別項* 不包含空白或其他無法接受的字元。  
  
## <a name="example"></a>範例  
 下列程式碼範例會產生錯誤訊息 C3345，因為 `name` 屬性的 `module` 參數包含空白。  
  
```  
// cpp_attr_name_module.cpp  
// compile with: /LD /link /OPT:NOREF  
#include <atlbase.h>  
#include <atlcom.h>  
#include <atlwin.h>  
#include <atltypes.h>  
#include <atlctl.h>  
#include <atlhost.h>  
#include <atlplus.h>  
  
// C3345 expected  
[module(dll, name="My Library", version="1.2", helpfile="MyHelpFile")]   
// Try the following line instead  
//[module(dll, name="MyLibrary", version="1.2", helpfile="MyHelpFile")]   
// Module attribute now applies to this class  
class CMyClass {  
public:  
BOOL WINAPI DllMain(DWORD dwReason, LPVOID lpReserved) {  
   // add your own code here  
   return __super::DllMain(dwReason, lpReserved);  
   }  
};  
```  
  
## <a name="see-also"></a>另請參閱  
 [__iscsym](../../c-runtime-library/reference/iscsym-functions.md)   
 [字元分類](../../c-runtime-library/character-classification.md)   
 [模組](../../windows/module-cpp.md)
