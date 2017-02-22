---
title: "在內嵌組譯碼中使用和保留暫存器 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__asm 關鍵字 [C++], 暫存器值"
  - "內嵌組譯碼, 暫存器"
  - "保留暫存器"
  - "暫存器, 內嵌組譯碼"
ms.assetid: dbcd7360-6f3e-4b22-9ee2-9f65ca6f2543
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 在內嵌組譯碼中使用和保留暫存器
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

## Microsoft 特定  
 一般情況下，您不應該假設暫存器將會有指定的值時`__asm`區塊開始。  暫存器值不一定會保留至不同的`__asm`區塊。  如果您結束的內嵌程式碼區塊，並開始另一個，您不能依賴保留它們的值從第一個區塊的第二個區塊中的暫存器。   `__asm`區塊會繼承任何註冊控制項的一般流程中的值結果。  
  
 如果您使用`__fastcall`呼叫慣例，編譯器會將傳遞函式引數在暫存器而不是在堆疊上。  這可以在函式中建立問題`__asm`因為函式有辦法知道是哪一個暫存器中的哪一個參數會封鎖。  如果函式剛好在 EAX 中收到參數，並立即將儲存在 EAX 中其他項目，原始的參數將會遺失。  此外，您必須保留在任何函式中以宣告的 ECX 暫存器 `__fastcall`.  
  
 若要避免這類登錄衝突，請勿使用`__fastcall`之函式包含的慣例  `__asm`區塊。  如果您指定`__fastcall`慣例使用 \/Gr 編譯器選項時，全域宣告每個函式包含  `__asm`區塊  `__cdecl`或  `__stdcall`.  \(  `__cdecl`屬性會告知編譯器該函式使用 C 呼叫慣例。\) 如果您編譯的不與 \/Gr，避免宣告的函式與`__fastcall`屬性。  
  
 當使用 `__asm`C\/c \+ \+ 函式中寫入組件語言，您不需要保留 EAX、 EBX、 ECX、 EDX、 ESI 或 EDI 暫存器。  例如，在 POWER2。在 C 範例[具有內嵌組譯碼的撰寫函式](../../assembler/inline/writing-functions-with-inline-assembly.md)、  `power2`函式並不會保留在 EAX 登錄中的值。  不過，使用這些暫存器會影響程式碼品質因為暫存器配置器無法使用它們來存放值用於`__asm`區塊。  此外，使用 EBX、 ESI EDI 中或內嵌組譯程式碼，您會強制編譯器儲存並還原在函式初構和終這些暫存器。  
  
 您應該保留其他您使用 \(例如 DS、 SS、 預存程序、 BP 和旗標的暫存器\) 的暫存器的範圍的`__asm`區塊。  除非您有一些變更，\(例如切換堆疊\) 的理由，您應該保留 ESP 和 EBP 暫存器。  請參閱[最佳化內嵌組譯碼](../../assembler/inline/optimizing-inline-assembly.md)。  
  
 某些 SSE 型別需要 8 個位元組的堆疊對齊方式，強制編譯器發出動態堆疊對齊程式碼。  若要對齊方式之後，存取本機變數和函式參數，編譯器會維護兩個框架指標。  如果編譯器執行框架指標省略 \(FPO\)，它會使用 EBP 及 ESP。  如果編譯器不會執行 FPO，它會使用 EBX 和 EBP。  若要正確地確保程式碼執行，請勿修改 EBX 組譯程式碼中如果函數需要動態堆疊對齊方式，因為它無法修改框架指標。  移動八個位元組對齊型別從函式，或避免使用 EBX。  
  
> [!NOTE]
>  如果您內嵌組譯程式碼變更使用的標準或 CLD 指示的方向旗標，您必須還原為其原始值的旗標。  
  
 **結束 Microsoft 特定**  
  
## 請參閱  
 [內嵌組譯工具](../../assembler/inline/inline-assembler.md)