---
title: "編譯器警告 (層級 1 和 3) C4793 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4793"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4793"
  - "C6630"
  - "C6631"
  - "C6634"
  - "C6635"
  - "C6636"
  - "C6637"
  - "C6638"
  - "C6639"
  - "C6640"
ms.assetid: 819ada53-1d9c-49b8-a629-baf8c12314e6
caps.latest.revision: 28
caps.handback.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1 和 3) C4793
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function'：函式以機器碼編譯：'reason'  
  
 編譯器無法將 *function* 編譯為 Managed 程式碼，即使已經指定 [\/clr](../../build/reference/clr-common-language-runtime-compilation.md) 編譯器選項。  編譯器反而會發出警告 C4793 和說明的接續訊息，然後將 *function* 編譯成機器碼。  這個接續訊息包含的 *reason* 文字，會說明 *function* 無法編譯成 `MSIL` 的原因。  
  
 這是在指定 `/clr:pure` 編譯器選項時的層級 1 警告。  
  
 下列表格列出所有可能的接續訊息。  
  
|原因訊息|備註|  
|----------|--------|  
|Managed 程式碼不支援對齊的資料型別|CLR 必須能夠視需要配置資料，而當資料與 [\_\_m128](../../cpp/m128.md) 或 [align](../../cpp/align-cpp.md) 這類的宣告對齊時可能無法進行配置。|  
|Managed 程式碼不支援使用 '\_\_ImageBase' 的函式|`__ImageBase` 是連結器符號，通常只會用於低階機器碼以載入 DLL。|  
|'\/clr' 編譯器選項不支援 varargs|原生函式無法呼叫具有[變數引數清單](../../misc/variable-argument-lists.md) \(varargs\) 的 Managed 函式，因為函式有不同的堆疊配置需求。  然而，如果指定 `/clr:pure` 編譯器選項，因為組件只可以包含 Managed 函式，所以可以支援變數引數清單。  如需詳細資訊，請參閱[純粹的和可驗證的程式碼](../../dotnet/pure-and-verifiable-code-cpp-cli.md)。|  
|64 位元 CLR 不支援以 \_\_ptr32 修飾詞宣告的資料|指標的大小必須與目前平台的原生指標相同。  如需詳細資訊，請參閱[\_\_ptr32、\_\_ptr64](../../cpp/ptr32-ptr64.md)。|  
|32 位元 CLR 不支援以 \_\_ptr64 修飾詞宣告的資料|指標的大小必須與目前平台的原生指標相同。  如需詳細資訊，請參閱[\_\_ptr32、\_\_ptr64](../../cpp/ptr32-ptr64.md)。|  
|Managed 程式碼不支援一個或多個內建|內建名稱在發生訊息時還無法使用。  然而，造成這個訊息的內建通常代表低階的機器指令。|  
|Managed 程式碼不支援內嵌原生組譯碼 \('\_\_asm'\)|[內嵌組譯程式碼](../../assembler/inline/asm.md)可以包含任意無法 Managed 的機器碼。|  
|非 \_\_clrcall 虛擬函式 Thunk 必須編譯為原生|非 [\_\_clrcall](../../cpp/clrcall.md) 虛擬函式 Thunk 必須使用 Unmanaged 位址。|  
|使用 '\_setjmp' 的函式必須編譯為原生|CLR 必須能夠控制程式執行。  然而，[setjmp](../../cpp/using-setjmp-longjmp.md) 函式藉由儲存和還原低階資訊 \(例如登錄和執行狀態\) 而會忽略一般程式執行。|  
  
## 範例  
 下列範例會產生 C4793。  
  
```  
// C4793.cpp  
// compile with: /c /clr /W3   
// processor: x86  
int asmfunc(void) {   // C4793, compiled as unmanaged, native code  
   __asm {  
      mov eax, 0  
   }  
}  
```  
  
  **警告 C4793：'asmfunc'：函式以機器碼編譯：**  
 **Managed 程式碼不支援內嵌原生組譯碼 \('\_\_asm'\)**   
## 範例  
 下列範例會產生 C4793。  
  
```  
// C4793_b.cpp  
// compile with: /c /clr /W3  
#include <setjmp.h>  
jmp_buf test_buf;  
  
void f() {  
   setjmp(test_buf);   // C4793 warning  
}  
```  
  
  **警告 C4793：'f'：函式以機器碼編譯：**  
 **使用 '\_setjmp' 的函式必須編譯為原生**