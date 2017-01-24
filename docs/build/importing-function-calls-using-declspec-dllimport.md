---
title: "使用 __declspec(dllimport) 匯入函式呼叫 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "__declspec"
  - "dllimport"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec(dllimport) 關鍵字 [C++]"
  - "dllimport 屬性 [C++], 函式呼叫匯入"
  - "函式呼叫 [C++], 匯入"
  - "匯入函式呼叫 [C++]"
ms.assetid: 6b53c616-0c6d-419a-8e2a-d2fff20510b3
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 使用 __declspec(dllimport) 匯入函式呼叫
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

下列程式碼範例將顯示如何使用 **\_declspec\(dllimport\)**，以便從 DLL 匯入函式呼叫到應用程式。  假設 `func1` 是位於 DLL 中的函式，此 DLL 和包含 **main** 函式的 .exe 檔位於不同位置。  
  
 請在不使用 **\_\_declspec\(dllimport\)** 情況下給定下列程式碼：  
  
```  
int main(void)   
{  
   func1();  
}  
```  
  
 編譯器所產生的程式碼看起來會像下面這樣：  
  
```  
call func1  
```  
  
 而連結器會將呼叫轉譯成像下面這樣的程式碼：  
  
```  
call 0x4000000         ; The address of 'func1'.  
```  
  
 如果 `func1` 存在於另一個 DLL，則連結器會因為無法得知 `func1` 的位址而無法直接解析。  在 16 位元環境裡，連結器會將這個程式碼位址加入至 .exe 中的清單，載入器會在執行階段以正確位址更正清單中的位址。  在 32 位元和 64 位元環境裡，連結器會產生它確實知道位址的 Thunk。  在 32 位元環境中，Thunk 看起來類似：  
  
```  
0x40000000:    jmp DWORD PTR __imp_func1  
```  
  
 此處 `imp_func1` 是 .exe 檔匯入位址表中 `func1` 位置的位址。  因此連結器會知道所有的位址。  載入器只需在載入時間 \(Load Time\) 更新 .exe 檔的匯入位址表，便可使所有步驟正確運作。  
  
 因此，使用 **\_\_declspec\(dllimport\)** 是比較好的做法，因為連結器在不需要使用時就不會產生 Thunk。  Thunk 會讓程式碼變大 \(在 RISC 系統中，它可能是許多指令\) 並可能降低您的快取 \(Cache\) 效能。  如果您告訴編譯器此函式位在 DLL 裡，它便可以為您產生間接的呼叫。  
  
 因此現在這段程式碼：  
  
```  
__declspec(dllimport) void func1(void);  
int main(void)   
{  
   func1();  
}  
```  
  
 會產生下面這個指令：  
  
```  
call DWORD PTR __imp_func1  
```  
  
 因為沒有 Thunk 和 `jmp` 指令，所以程式碼會較小並執行更快。  
  
 另一方面，對於 DLL 內的函式呼叫，您並不需要使用間接呼叫。  您已經知道函式的位址。  因為在間接呼叫之前，載入和儲存函式的位址會需要時間和空間，所以直接呼叫一定會較快和較小。  您只需要在要從 DLL 本身外部呼叫 DLL 函式時使用 **\_\_declspec\(dllimport\)**。  在建置 DLL 時，不要在 DLL 內部的函式上使用 **\_\_declspec\(dllimport\)**。  
  
## 請參閱  
 [匯入至應用程式](../build/importing-into-an-application.md)