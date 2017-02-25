---
title: "連結器工具警告 LNK4253 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4253"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4253"
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 連結器工具警告 LNK4253
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

區段 'section1' 尚未合併到 'section2'，但已經合併到 'section3'  
  
 連結器偵測到多個互相衝突的合併要求。  連結器將忽略其中一個要求。  
  
 遇到 **\/MERGE** 選項或指示詞，而且由於先前的 **\/MERGE** 選項或指示詞 \(或是由於連結器的隱含合併\)，`from` 區段已經合併入不同的區段。  
  
 若要解決 LNK4253 錯誤，請移除其中一個合併要求。  
  
 當您以 x86 機器和具有 Visual C\+\+ 的 Windows CE \(ARM、MIPS、SH4 和 Thumb\) 為目標時，則 .CRT 區段現在會是唯讀的。  如果程式碼依賴之前的行為 \(.CRT 區段為讀取\/寫入\)，您可能會看到非預期的行為。  
  
 如需詳細資訊，請參閱：  
  
-   [\/MERGE \(結合區段\)](../../build/reference/merge-combine-sections.md)  
  
-   [註解](../../preprocessor/comment-c-cpp.md)  
  
## 範例  
 在下列範例中，連結器接到指示，要合併 `.rdata` 區段兩次，但要併入不同的區段中。  下列範例會產生 LNK4253。  
  
```  
// LNK4253.cpp  
// compile with: /W1 /link /merge:.rdata=text2  
// LNK4253 expected  
#pragma comment(linker, "/merge:.rdata=.text")  
int main() {}  
```