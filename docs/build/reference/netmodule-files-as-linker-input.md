---
title: ".netmodule 檔作為連結器輸入 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- MSIL linking
- linking [C++], modules
- .netmodules
- modules, Visual C++
ms.assetid: a4bcbe8a-4255-451d-853b-f88cfd82f4e1
caps.latest.revision: "22"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 7b07e82fe8d7d191dc328645efd99ab3a9a4f6fc
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="netmodule-files-as-linker-input"></a>.netmodule 檔做為連結器輸入
link.exe 現在接受 MSIL .obj 或 .netmodule 做為輸入。 連結器產生的輸出檔將是組件或 .netmodule，對連結器的任何輸入 .obj 或 .netmodule 沒有執行階段相依性。  
  
 由 Visual c + + 編譯器，以建立.netmodule [/LN （建立 MSIL 模組）](../../build/reference/ln-create-msil-module.md)或與連結器[/NOASSEMBLY （建立 MSIL 模組）](../../build/reference/noassembly-create-a-msil-module.md)。 .obj 一律會建立在 Visual c + + 編譯中。 對於其他 Visual Studio 編譯器中，使用**/target: module**編譯器選項。  
  
 在大部分情況下，您必須從傳遞至連結器.obj 檔案建立.netmodule，Visual c + + 編譯以建立.netmodule 除非[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)。 做為連結器的輸入必須是純 MSIL，可以利用 Visual c + + 編譯器產生 MSIL.netmodule **/clr: safe**。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。 .NET Visual Studio 編譯器都會產生純 MSIL 模組預設。  
  
 如需如何叫用連結器，從命令列資訊，請參閱[連結器命令列語法](../../build/reference/linker-command-line-syntax.md)，[命令列上的建置 C/c + + 程式碼](../../build/building-on-the-command-line.md)，和[設定的路徑和環境變數命令列建置](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)。  
  
 .Netmodule 或.dll 檔案傳遞至連結器所使用 Visual c + + 編譯器編譯**/clr**或**/clr: pure**可能會導致連結器錯誤。 如需詳細資訊，請參閱[選擇.netmodule 輸入的檔案格式](../../build/reference/choosing-the-format-of-netmodule-input-files.md)。  
  
 連結器接受原生.obj 檔案，以及所編譯的 MSIL 的.obj 檔**/clr**， **/clr: pure**，或**/clr: safe**。 將 resxdatanodes 傳遞混合的.obj 相同組建中，產生的輸出檔案的可驗證性，根據預設，會等於輸入模組的可驗證性的最低層級。 比方說，如果您將安全和純.obj 傳遞至連結器時，輸出檔就是純虛擬。 [/CLRIMAGETYPE （指定類型的 CLR 映像）](../../build/reference/clrimagetype-specify-type-of-clr-image.md)可讓您指定較低層級的可驗證性，如果您的需要。  
  
 如果您目前擁有由兩個或多個組件組成的應用程式，而您要讓應用程式包含在一個組件中，您必須重新編譯組件，然後連結 .obj 或 .netmodule，以產生單一組件。  
  
 您必須指定進入點使用[/ENTRY （進入點符號）](../../build/reference/entry-entry-point-symbol.md)建立可執行映像時。  
  
 當連結的 MSIL 的.obj 或.netmodule 檔，使用[/LTCG （連結時間程式碼產生）](../../build/reference/ltcg-link-time-code-generation.md)，否則當連結器遇到 MSIL 的.obj 或.netmodule 時，它會重新啟動以 /LTCG 連結。  
  
 MSIL .obj 或 .netmodule 檔案也可以傳遞給 cl.exe。  
  
 輸入 MSIL .obj 或 .netmodule 檔案無法具有內嵌資源。 資源內嵌在輸出檔案 （模組或組件）[與 /ASSEMBLYRESOURCE （內嵌 Managed 資源）](../../build/reference/assemblyresource-embed-a-managed-resource.md)連結器選項或**/resource**在其他 Visual Studio 編譯器編譯的編譯器選項。  
  
 當執行 MSIL 連結，而且也未指定[/LTCG （連結時間程式碼產生）](../../build/reference/ltcg-link-time-code-generation.md)，您會看到告知性訊息報告正在重新啟動連結。 這則訊息可以被忽略，但若要連結器的效能改善 MSIL 連結，明確指定**/LTCG**。  
  
## <a name="example"></a>範例  
 在 c + + 程式碼中的對應 try catch 區塊會叫用的非系統例外狀況。 不過，根據預設，CLR 會包裝與非系統例外狀況<xref:System.Runtime.CompilerServices.RuntimeWrappedException>。 當組件從 Visual c + + 建立，而且非 Visual c + + 模組，並且想要在 c + + 程式碼時要叫用從其對應的 try 子句的 try 區塊就會擲回非系統例外狀況，您必須加入一個 catch 區塊  
  
 [assembly:System::Runtime::CompilerServices::RuntimeCompatibility(WrapNonExceptionThrows=false)] 屬性套用至非 c + + 模組的原始程式碼。  
  
```  
// MSIL_linking.cpp  
// compile with: /c /clr  
value struct V {};  
  
ref struct MCPP {  
   static void Test() {  
      try {  
         throw (gcnew V);  
      }  
      catch (V ^) {  
         System::Console::WriteLine("caught non System exception in C++ source code file");  
      }  
   }  
};  
  
/*  
int main() {  
   MCPP::Test();  
}  
*/  
```  
  
## <a name="example"></a>範例  
 藉由變更 WrapNonExceptionThrows 屬性的布林值，您可以修改 Visual c + + 程式碼能夠攔截非系統例外狀況。  
  
```  
// MSIL_linking_2.cs  
// compile with: /target:module /addmodule:MSIL_linking.obj  
// post-build command: link /LTCG MSIL_linking.obj MSIL_linking_2.netmodule /entry:MLinkTest.Main /out:MSIL_linking_2.exe /subsystem:console  
using System.Runtime.CompilerServices;  
  
// enable non System exceptions  
[assembly:RuntimeCompatibility(WrapNonExceptionThrows=false)]  
  
class MLinkTest {  
   public static void Main() {  
      try {  
         MCPP.Test();  
      }  
      catch (RuntimeWrappedException) {  
         System.Console.WriteLine("caught a wrapped exception in C#");  
      }  
   }  
}  
```  
  
```Output  
caught non System exception in C++ source code file  
```  
  
## <a name="see-also"></a>另請參閱  
 [LINK 輸入的檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)