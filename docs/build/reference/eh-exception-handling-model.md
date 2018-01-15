---
title: "-EH （例外狀況處理模型） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExceptionHandling
- /eh
- VC.Project.VCCLCompilerTool.ExceptionHandling
dev_langs: C++
helpviewer_keywords:
- exception handling, compiler model
- cl.exe compiler, exception handling
- EH compiler option [C++]
- -EH compiler option [C++]
- /EH compiler option [C++]
ms.assetid: 754b916f-d206-4472-b55a-b6f1b0f2cb4d
caps.latest.revision: "29"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1c56020d5013e951d9d43ed799d34641d114d612
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="eh-exception-handling-model"></a>/EH (例外狀況處理模型)
指定編譯器所使用的例外狀況處理類型、何時要繼續最佳化例外狀況檢查，以及是否要終結因例外狀況而超出範圍的 C++ 物件。 如果沒有指定 **/EH** ，編譯器就會同時攔截非同步結構化例外狀況和 C++ 例外狀況，但不會終結因非同步例外狀況而超出範圍的 C++ 物件。  
  
## <a name="syntax"></a>語法  
  
```  
/EH{s|a}[c][r][-]  
```  
  
## <a name="arguments"></a>引數  
 **a**  
 同時攔截非同步 (結構化) 例外狀況和同步 (C++) 例外狀況的例外狀況處理模型。  
  
 **s**  
 只會攔截 C++ 例外狀況，並告知編譯器假設宣告為 `extern "C"` 的函式可能會擲回例外狀況的例外狀況處理模型。  
  
 **C**  
 如果搭配 **s** (**/EHsc**) 使用，便只會攔截 C++ 例外狀況，並告知編譯器假設宣告為 `extern "C"` 的函式永遠不會擲回 C++ 例外狀況。  
  
 **/EHca** 相當於 **/EHa**。  
  
 **r**  
 告知編譯器針對所有 `noexcept` 函式一律產生執行階段終止檢查。 根據預設，如果編譯器判斷函式只會呼叫非擲回函式，則可能會繼續最佳化 `noexcept` 的執行階段檢查。  
  
## <a name="remarks"></a>備註  
 **/EHa** 編譯器選項可搭配原生 C++ `catch(...)` 子句，用來支援非同步結構化例外狀況處理 (SEH)。 若要實作 SEH 而不指定 **/EHa**，您可以使用 `__try`、 `__except`、 and `__finally` 語法。 雖然 Windows 和 Visual C++ 支援 SEH，但強烈建議您使用 ISO 標準 C++ 例外狀況處理 (**/EHs** 或 **/EHsc**)，因為它可提升程式碼的可攜性和彈性。 不過，在現有程式碼，或針對特定類型的程式 — 例如，在程式碼編譯為支援 common language runtime ([/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)) — 您仍然必須使用 SEH。 如需詳細資訊，請參閱 [Structured Exception Handling (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)。  
  
 使用 **/EHa** 指定 `catch(...)` 並嘗試處理所有例外狀況可能並不安全。 在大部分情況下，非同步例外狀況無法復原，因此應視為嚴重。 攔截這些例外狀況並繼續執行可能造成處理序損毀，因而導致難以找出並修正的 Bug。  
  
 如果您使用 **/EHs** 或 **/EHsc**，那麼您的 `catch(...)` 子句就不會攔截非同步結構化例外狀況。 存取違規和 Managed <xref:System.Exception?displayProperty=fullName> 例外狀況並不會遭到攔截，而產生非同步例外狀況時不會終結範圍內的物件，即使已處理非同步例外狀況也一樣。  
  
 如果您使用 **/EHa**，由於編譯器不會積極地最佳化 `try` 區塊，因此影像可能較大且執行效能可能較低。 即使編譯器未發現任何可能擲回 C++ 例外狀況的程式碼，仍會在例外況狀中留下自動呼叫所有本機物件之解構函式的篩選。 這樣就能安全地回溯非同步例外狀況以及 C++ 例外狀況的堆疊。 當您使用 **/EHs**時，編譯器會假設例外狀況只能在 `throw` 陳述式或在函式呼叫中出現。 這樣編譯器就能夠消除追蹤許多無法回溯物件之存留期的程式碼，進而大幅縮小程式碼。  
  
 建議您不要在相同可執行模組中，將使用 **/EHa** 編譯的物件與使用 **/EHs** 編譯的物件連結在一起。 如果您必須在模組中的任何位置使用 **/EHa** 處理非同步例外狀況，請使用 **/EHa** 編譯模組中的所有程式碼。 您可以在與使用 **/EHs**編譯的程式碼所在位置相同的模組中使用結構化例外狀況處理語法，但是不能在相同函式中混用 SEH 語法與 `try`、 `throw`和 `catch` 。  
  
 如果您要攔截並非 **/EHa** 所引發的例外狀況，請使用 `throw`。 這個範例將會產生並攔截結構化例外狀況：  
  
```cpp  
// compiler_options_EHA.cpp  
// compile with: /EHa  
#include <iostream>  
#include <excpt.h>  
using namespace std;  
  
void fail() {   // generates SE and attempts to catch it using catch(...)  
   try {  
      int i = 0, j = 1;  
      j /= i;   // This will throw a SE (divide by zero).  
      printf("%d", j);   
   }  
   catch(...) {   // catch block will only be executed under /EHa  
      cout<<"Caught an exception in catch(...)."<<endl;  
   }  
}  
  
int main() {  
   __try {  
      fail();   
   }  
  
   // __except will only catch an exception here  
   __except(EXCEPTION_EXECUTE_HANDLER) {     
   // if the exception was not caught by the catch(...) inside fail()  
      cout << "An exception was caught in __except." << endl;  
   }  
}  
```  
  
 **/EHc** 選項要求必須指定 **/EHs** 或 **/EHa** 。 **/clr** 選項表示 **/EHa** (也就是 **/clr /EHa** 是多餘的)。 如果在 **/clr** 之後使用 **/EHs[c]**，編譯器就會產生錯誤。 最佳化作業不會影響這種行為。 攔截到例外狀況時，編譯器會叫用類別解構函式，或是與例外狀況位於相同範圍中的一個或多個物件的解構函式。 如果未攔截到例外狀況，則不會執行這些解構函式。  
  
 如需 **/clr**下的例外狀況處理限制的相關資訊，請參閱 [_set_se_translator](../../c-runtime-library/reference/set-se-translator.md)。  
  
 使用 **-**符號就可以清除選項。 例如， **/EHsc-** 會解譯為 **/EHs /EHc-** ，相當於 **/EHs**。  
  
 **/EHr** 編譯器選項會在所有具有 `noexcept` 屬性的函式中，強制執行執行階段終止檢查。 根據預設，如果編譯器後端判斷函式只會呼叫 *「非擲回」* (Non-throwing) 函式，則可能會繼續最佳化執行階段檢查。 非擲回函式是具有指定不會擲回任何例外狀況之屬性的任何函式。 其中包含標示為 `noexcept`、 `throw()`、 `__declspec(nothrow)`的函式，以及指定 **/EHc** 時的 `extern "C"` 函式一律產生執行階段終止檢查。 非擲回函式也包含編譯器判定檢查不會擲回任何例外狀況的任何函式。 您可以使用 **/EHr-**明確地設定預設值。  
  
 不過，非擲回屬性並不保證函式不會擲回任何例外狀況。 不同於 `noexcept` 函式的行為，Visual C++ 編譯器會將使用 `throw()`、 `__declspec(nothrow)`或 `extern "C"` 宣告之函式所擲回的例外狀況，視為未定義的行為。 使用這三種宣告屬性的函式，不會對例外狀況強制執行執行階段終止檢查。 您可以使用 **/EHr** 選項來識別這項未定義的行為，方法是強制編譯器針對逸出 `noexcept` 函式的未處理例外狀況，產生執行階段檢查。  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  在左窗格中，展開 [組態屬性] 、[C/C++] 、[程式碼產生] 。  
  
3.  修改 [啟用 C++ 例外狀況]  屬性。  
  
     或者，將 [啟用 C++ 例外狀況]  設定為 [否] ，然後在 [命令列]  屬性頁的 [其他選項]  方塊中，加入編譯器選項。  
  
### <a name="to-set-this-compiler-option-programmatically"></a>若要以程式方式設定這個編譯器選項  
  
-   請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExceptionHandling%2A>。  
  
## <a name="see-also"></a>請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)   
 [錯誤和例外狀況處理](../../cpp/errors-and-exception-handling-modern-cpp.md)   
 [例外狀況規格 (throw)](../../cpp/exception-specifications-throw-cpp.md)   
 [結構化例外狀況處理 (C/C++)](../../cpp/structured-exception-handling-c-cpp.md)