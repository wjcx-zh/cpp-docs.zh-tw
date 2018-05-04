---
title: noreturn |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- noreturn_cpp
dev_langs:
- C++
helpviewer_keywords:
- __declspec keyword [C++], noreturn
- noreturn __declspec keyword
ms.assetid: 9c6517e5-22d7-4051-9974-3d2200ae4d1d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90fab865a02b7ad00bd25b6d74f2d19b2678875c
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="noreturn"></a>noreturn
## <a name="microsoft-specific"></a>Microsoft 特定的  
 這個 `__declspec` 屬性會告知編譯器函式不會傳回。 因此，編譯器知道，呼叫的程式碼 **__declspec （noreturn)** 函式是不可能執行到。  
  
 如果編譯器發現某個函式包含的控制路徑不會傳回值，則會產生警告 (C4715) 或錯誤訊息 (C2202)。 如果無法到達控制路徑，因為不會傳回的函式，您可以使用 **__declspec （noreturn)** 來避免這個警告或錯誤。  
  
> [!NOTE]
>  加入 **__declspec （noreturn)** 預期會傳回的函式可能會導致未定義的行為。  
  
## <a name="example"></a>範例  
 在下列範例中， **else**子句不包含 return 陳述式。  宣告`fatal`為 **__declspec （noreturn)** 可避免錯誤或警告訊息。  
  
```  
// noreturn2.cpp  
__declspec(noreturn) extern void fatal () {}  
  
int main() {  
   if(1)  
     return 1;  
   else if(0)  
     return 0;  
   else  
     fatal();  
}  
```  
  
## <a name="see-also"></a>另請參閱  
 [__declspec](../cpp/declspec.md)   
 [關鍵字](../cpp/keywords-cpp.md)