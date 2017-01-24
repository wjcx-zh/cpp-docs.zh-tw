---
title: "引數傳遞和命名慣例 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "傳遞引數 [C++], 慣例"
  - "引數 [C++], 命名"
  - "引數 [C++], 傳遞"
  - "引數 [C++], 擴展"
  - "編碼慣例, 引數"
  - "慣例 [C++], 引數名稱"
  - "命名慣例 [C++], 引數"
  - "傳遞引數, 慣例"
  - "暫存器, 傳回值"
  - "thiscall 關鍵字 [C++]"
ms.assetid: de468979-eab8-4158-90c5-c198932f93b9
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 引數傳遞和命名慣例
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 Visual C\+\+ 編譯器允許您指定在函式和呼叫端之間傳遞引數和傳回值的慣例。  並非所有慣例都適用於所有支援的平台，部分慣例會使用平台特定實作。  在大部分情況下，會忽略在特定平台上指定不支援慣例的關鍵字或編譯器參數，並且使用平台預設慣例。  
  
 在 x86 平台上傳遞引數時，會將所有引數擴大為 32 位元。  傳回值也會被擴大為 32 位元並在 EAX 暫存器中傳回，但 8 位元組結構例外，它是在 EDX:EAX 暫存器組中傳回。  較大的結構會在 EAX 暫存器中以隱藏傳回結構的指標傳回。  參數會從右至左推送至堆疊。  非 POD 的結構不會在暫存器中傳回。  
  
 如果在函式中使用 ESI、EDI、EBX 和 EBP 暫存器，編譯器會產生初構和終解程式碼來儲存和還原這些暫存器。  
  
> [!NOTE]
>  從函式以傳值方式傳回結構、等位或類別時，類型的所有定義必須相同，否則程式可能會在執行階段失敗。  
  
 如需如何定義自己的函式初構和終解程式碼的詳細資訊，請參閱 [naked 函式呼叫](../cpp/naked-function-calls.md)。  
  
 如需有關以 x64 平台為目標之程式碼中的預設呼叫慣例的詳細資訊，請參閱 [x64 呼叫慣例概觀](../build/overview-of-x64-calling-conventions.md)。  如需有關以 ARM 平台為目標之程式碼中的呼叫慣例問題的詳細資訊，請參閱[Visual C\+\+ ARM 移轉時常見的問題](../build/common-visual-cpp-arm-migration-issues.md)。  
  
 Visual C\/C\+\+ 編譯器支援下列呼叫慣例。  
  
|關鍵字|堆疊清除|參數傳遞|  
|---------|----------|----------|  
|[\_\_cdecl](../cpp/cdecl.md)|呼叫端|以相反順序 \(從右至左\) 將參數推送至堆疊|  
|[\_\_clrcall](../cpp/clrcall.md)|N\/A|依照順序 \(從左至右\) 將參數載入至 CLR 運算式堆疊。|  
|[\_\_stdcall](../cpp/stdcall.md)|被呼叫端|以相反順序 \(從右至左\) 將參數推送至堆疊|  
|[\_\_fastcall](../cpp/fastcall.md)|被呼叫端|儲存在暫存器中，然後推送至堆疊|  
|[\_\_thiscall](../cpp/thiscall.md)|被呼叫端|推送到堆疊；將 **this** 指標儲存在 ECX 中|  
|[\_\_vectorcall](../cpp/vectorcall.md)|被呼叫端|儲存在暫存器中，然後以相反順序 \(從右至左\) 推送至堆疊|  
  
 如需相關資訊，請參閱[過時呼叫慣例](../cpp/obsolete-calling-conventions.md)。  
  
 **END Microsoft 特定的**  
  
## 請參閱  
 [呼叫慣例](../cpp/calling-conventions.md)