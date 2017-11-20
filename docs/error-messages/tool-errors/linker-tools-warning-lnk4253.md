---
title: "連結器工具警告 LNK4253 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4253
dev_langs: C++
helpviewer_keywords: LNK4253
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: fe7e60c3066e2981f1b826381691950b2ccd46d3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4253"></a>連結器工具警告 LNK4253
區段 'section1' 尚未合併到 'section2';已合併到 'section3'  
  
 連結器偵測到多個衝突的合併要求。 連結器將會忽略其中一個要求。  
  
 A **/合併**遇到選項或指示詞和`from`> 一節已合併入不同的區段，因為前一個**/合併**選項或指示詞 （或從隱含合併連結器）。  
  
 若要解決 LNK4253，移除其中一個合併要求。  
  
 當以 x86 為目標電腦和 Visual c + +，（ARM、 MIPS、 SH4 和縮圖） 的 Windows CE 目標。CRT 區段現在是唯讀屬性。 如果您的程式碼相依於先前的行為 (。CRT 區段是讀取/寫入），您就可以看到未預期的行為。  
  
 如需詳細資訊，請參閱：  
  
-   [/MERGE （結合區段）](../../build/reference/merge-combine-sections.md)  
  
-   [comment (C/C++)](../../preprocessor/comment-c-cpp.md)  
  
## <a name="example"></a>範例  
 在下列範例中，連結器會指示合併`.rdata`區段兩次，但為不同的區段。 下列範例會產生 LNK4253。  
  
```  
// LNK4253.cpp  
// compile with: /W1 /link /merge:.rdata=text2  
// LNK4253 expected  
#pragma comment(linker, "/merge:.rdata=.text")  
int main() {}  
```