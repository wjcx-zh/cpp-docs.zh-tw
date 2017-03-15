---
title: "編譯器錯誤 C2065 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2065
dev_langs:
- C++
helpviewer_keywords:
- C2065
ms.assetid: 78093376-acb7-45f5-9323-5ed7e0aab1dc
caps.latest.revision: 20
author: corob-msft
ms.author: corob
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
translationtype: Machine Translation
ms.sourcegitcommit: 3f69f0c3176d2fbe19e11ce08c071691a72d858d
ms.openlocfilehash: 81686df4727ab2b3d5af749174a42016e8443e70
ms.lasthandoff: 02/24/2017

---
# <a name="compiler-error-c2065"></a>編譯器錯誤 C2065
'identifier'：未宣告的識別項  
  
 必須先在宣告中指定變數的類型，才可加以使用。 必須先在宣告或原型中指定函式使用的參數，才可使用此函式。  
  
 可能的原因：  
  
1.  識別項名稱拼錯了。  
  
2.  識別項使用錯誤的大寫和小寫字母。  
  
3.  遺漏字串常數之後的右引號。  
  
4.  您使用編譯偵錯版本的 C 執行階段中，宣告中的 c + + 標準程式庫迭代器變數`for`迴圈，然後再嘗試使用該迭代器變數的範圍外`for`迴圈。 編譯 c + + 標準程式庫的 C 執行階段的偵錯版本的程式碼所示[/zc: forscope](../../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md)。  請參閱[偵錯迭代器支援](../../standard-library/debug-iterator-support.md)如需詳細資訊。  
  
5.  您可能會在您的建置環境中目前不支援的 SDK 標頭檔中呼叫函式。  
  
6.  省略所需的 Include 檔案，特別是當您定義 `VC_EXTRALEAN`、`WIN32_LEAN_AND_MEAN`或 `WIN32_EXTRA_LEAN` 時。 這些符號會從 windows.h 和 afxv_w32.h 中排除某些標頭檔，以加速編譯。 (在 windows.h 和 afxv_w32.h 中尋找所排除項目的最新描述)。  
  
7.  不當的命名空間範圍。 例如，若要解析不完整的 C++ Standard 程式庫函式和運算子，您必須透過 `using` 指示詞指定 `std` 命名空間。 下列範例無法編譯，因為 `using` 指示詞已註解排除，而 `cout` 已定義於 `std` 命名空間：  
  
## <a name="example"></a>範例  
 下列範例會產生 C2065，並示範如何修正此問題。  
  
```  
// C2065.cpp  
// compile with: /EHsc  
// using namespace std;   // Uncomment this line to fix  
#include <iostream>  
int main() {  
   cout << "Hello" << endl;   // C2065  
  
   // Or try the following line instead  
   std::cout << "Hello" << std::endl;  
}  
```  
  
## <a name="example"></a>範例  
 呼叫泛型函式時，如果無法從使用的參數推論預定的型別引數，則編譯器會回報錯誤。 如需詳細資訊，請參閱[泛型函式 (C + + /cli CLI)](../../windows/generic-functions-cpp-cli.md)。  
  
 下列範例會產生 C2065，並示範如何修正此問題。  
  
```  
// C2065_b.cpp  
// compile with: /clr  
generic <typename ItemType>  
void G(int i) {}  
  
int main() {  
   // global generic function call  
   G<T>(10);   // C2065  
   G<int>(10);   // OK - fix with a specific type argument  
}  
```  
  
## <a name="example"></a>範例  
 針對 Visual C++ 2005 所進行的編譯器一致性工作，也可能會導致這個錯誤：Visual C++ 屬性的參數檢查。  
  
 下列範例會產生 C2065，並示範如何修正此問題。  
  
```  
// C2065_c.cpp  
// compile with: /c  
[module(DLL, name=MyLibrary)];   // C2065  
// try the following line instead  
// [module(dll, name="MyLibrary")];  
  
[export]  
struct MyStruct {  
   int i;  
};  
```
