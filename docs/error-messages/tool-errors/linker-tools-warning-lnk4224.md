---
title: "連結器工具警告 LNK4224 | Microsoft Docs"
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
  - "LNK4224"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4224"
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具警告 LNK4224
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

不再支援 option；已忽略  
  
 指定了一個無效、過時的連結器選項，已忽略該選項。  
  
 例如，如果有 \/comment 指示詞出現在 .obj 檔中，則可能會發生 LNK4224。  \/comment 指示詞應該已經使用已取代的 exestr 選項，由 [註解](../../preprocessor/comment-c-cpp.md) pragma 加入。  請使用 dumpbin [\/ALL](../../build/reference/all.md)，檢視 .obj 檔中的連結器指示詞。  
  
 可能的話，請修改 .obj 檔的來源並移除 pragma。  如果您忽略這項警告，可能會導致以 **\/clr:pure** 編譯的可執行檔無法如預期地執行。  
  
## 範例  
 下列範例會產生 LNK4224。  
  
```  
// LNK4224.cpp  
// compile with: /c /Zi  
// post-build command: link LNK4224.obj /debug /debugtype:map  
int main () {  
   return 0;  
}  
```