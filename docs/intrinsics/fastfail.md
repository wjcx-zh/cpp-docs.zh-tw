---
title: "__fastfail | Microsoft Docs"
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
ms.assetid: 9cd32639-e395-4c75-9f3a-ac3ba7f49921
caps.latest.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 3
---
# __fastfail
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Microsoft 特定的**  
  
 立即終止額外負荷最小的呼叫處理序。  
  
## 語法  
  
```  
void __fastfail(unsigned int code);  
```  
  
#### 參數  
 \[in\] `code`  
 winnt.h 或 wdm.h 中指出處理序終止原因的 `FAST_FAIL_<description>` 符號常數。  
  
## 傳回值  
 `__fastfail` 內建函式不會返回。  
  
## 備註  
 `__fastfail` 內建函式提供一種*「快速失敗」*\(fast fail\) 要求機制，這是一種讓可能已損毀的處理序要求立即終止處理序的方式。  一般例外狀況處理功能無法處理程式狀態可能已損毀和超越堆疊復原的嚴重失敗。  使用 `__fastfail` 終止使用最少額外負荷的處理序。  
  
 在內部方面，會使用數種架構特定機制來實作 `__fastfail`：  
  
|架構|指令|程式碼引數的位置|  
|--------|--------|--------------|  
|x86|int 0x29|ecx|  
|[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]|int 0x29|rcx|  
|ARM|Opcode 0xDEFB|r0|  
  
 快速失敗要求是獨立的，通常僅需要執行兩個指令。  執行快速失敗要求後，核心就會採取適當的動作。  在使用者模式程式碼中，當引發快速失敗事件時，沒有超出指令指標本身的記憶體相依性。  即使有嚴重的記憶體損毀，這仍可會使其可靠性達到最大。  
  
 `code` 引數是 winnt.h 或 wdm.h 中的其中一個 `FAST_FAIL_<description>` 符號常數，說明失敗狀況的類型，並以環境特定的方式併入失敗報告中。  
  
 使用者模式快速失敗要求會顯示為第二次機會非可持續例外狀況，具有例外狀況代碼 0xC0000409 及至少一個例外狀況參數。  第一個例外狀況參數是 `code` 值。  這個例外狀況代碼會向 Windows 錯誤報告 \(WER\) 和偵錯基礎結構指出處理序已損毀，且應該採取最小同處理序動作以回應失敗。  核心模式快速失敗要求是藉由使用專用的檢查錯誤程式碼 `KERNEL_SECURITY_CHECK_FAILURE`\(0x139\) 來實作。  在這兩種情況下，都不會叫用例外狀況處理常式，因為是預期程式要處於損毀的狀態。  如果存在偵錯工具，會賦予它機會在終止之前檢查程式的狀態。  
  
 從 Windows 8 開始支援原生快速失敗機制。  原本不支援快速失敗指令的 Windows 作業系統通常會將快速失敗要求視為存取違規或 `UNEXPECTED_KERNEL_MODE_TRAP` 檢查錯誤處理。  在這些情況下，此程式仍然會終止，但不一定會快速終止。  
  
 `__fastfail` 僅可作為內建函式使用。  
  
## 需求  
  
|內建|架構|  
|--------|--------|  
|`__fastfail`|x86、[!INCLUDE[vcprx64](../assembler/inline/includes/vcprx64_md.md)]、ARM|  
  
 **標頭檔** \<intrin.h\>  
  
## END Microsoft 特定的  
  
## 請參閱  
 [編譯器內建](../intrinsics/compiler-intrinsics.md)