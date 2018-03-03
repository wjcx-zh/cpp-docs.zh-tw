---
title: "編譯器錯誤 C3345 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C3345
dev_langs:
- C++
helpviewer_keywords:
- C3345
ms.assetid: 1dda4c79-73bb-441b-b939-746154c3afba
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ca51e90d8c0cbb1806cc0b042d9c3ae2480a9729
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [__iscsym](../../c-runtime-library/reference/iscsym-functions.md)   
 [字元分類](../../c-runtime-library/character-classification.md)   
 [模組](../../windows/module-cpp.md)