---
title: "-Zc: rvalueCast （強制型別轉換規則） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
dev_langs: C++
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8f4b888dde70708ee10b2d8000ff6380709dc870
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (強制型別轉換規則)
當**/zc: rvaluecast**指定選項時，編譯器正確識別右值參考類型為符合 C + + 11 標準轉換運算的結果。 當未指定該選項時，編譯器的行為會與 Visual Studio 2012 中的行為相同。 根據預設， **/zc: rvaluecast**已關閉。 為了取得一致性和消除使用轉型中的錯誤，我們建議您使用**/zc: rvaluecast**。  
  
## <a name="syntax"></a>語法  
  
```  
/Zc:rvalueCast[-]  
```  
  
## <a name="remarks"></a>備註  
 如果**/zc: rvaluecast**指定，則編譯器會遵循 C + + 11 標準的 5.4 節，並僅會視為轉型運算式導致非參考類型，且轉換導致非函式類型右值參考的運算式做為右值型別。 根據預設，或者如果**/Zc:rvalueCast-**指定，則編譯器會不一致，並將導致右值參考當做右值的所有轉型運算式。  
  
 使用**/zc: rvaluecast**如果您轉型運算式作為引數傳遞至採用右值參考類型的函式。 預設行為會導致編譯器錯誤[C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md)編譯器錯誤地判定轉型運算式的類型。 此範例顯示未指定 /Zc:rvalueCast 時，正確程式碼中的編譯器錯誤。  
  
```cpp  
// Test of /Zc:rvalueCast  
// compile by using:  
// cl /c /Zc:rvalueCast- make_thing.cpp  
// cl /c /Zc:rvalueCast make_thing.cpp  
  
#include <utility>  
  
template <typename T>   
struct Thing {  
   // Construct a Thing by using two rvalue reference parameters  
   Thing(T&& t1, T&& t2)  
      : thing1(t1), thing2(t2) {}  
  
   T& thing1;  
   T& thing2;  
};  
  
// Create a Thing, using move semantics if possible  
template <typename T>  
Thing<T> make_thing(T&& t1, T&& t2)  
{  
   return (Thing<T>(std::forward<T>(t1), std::forward<T>(t2)));  
}  
  
struct Test1 {  
   long a;  
   long b;  
  
   Thing<long> test() {   
      // Use identity casts to create rvalues as arguments  
      return make_thing(static_cast<long>(a), static_cast<long>(b));   
   }  
};  
  
```  
  
 適當時，預設編譯器行為可能不會報告錯誤 C2102。 在此範例中，編譯器不會報告錯誤時取得的位址建立身分轉型是右值如果**/zc: rvaluecast**未指定：  
  
```cpp  
int main() {  
   int a = 1;  
   int *p = &a;   // Okay, take address of lvalue   
                  // Identity cast creates rvalue from lvalue;    
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value  
}  
```  
  
 如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  選取**C/c + +**資料夾。  
  
3.  選取**命令列**屬性頁。  
  
4.  修改**其他選項**屬性，以包括**/zc: rvaluecast** ，然後選擇 **確定**。  
  
## <a name="see-also"></a>請參閱  
 [/Zc (一致性)](../../build/reference/zc-conformance.md)