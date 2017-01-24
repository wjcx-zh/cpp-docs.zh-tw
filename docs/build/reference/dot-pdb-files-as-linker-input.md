---
title: ".Pdb 檔做為連結器輸入 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - ".pdb 檔案, 做為連結器輸入"
  - "PDB 檔案, 做為連結器輸入"
ms.assetid: c1071478-2369-4b03-9df8-71761cf82f3b
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# .Pdb 檔做為連結器輸入
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

使用 \/Zi 選項編譯的目的檔 \(.obj\) 含有程式資料庫 \(PDB\) 的名稱。  您不用指定目的 PDB 檔名給連結器；必要時 LINK 會使用內嵌的名稱以尋找 PDB。  這也適用於程式庫中所含的可偵錯目的檔；可偵錯程式庫的 PDB 必須與程式庫一起可供連結器使用。  
  
 LINK 也會使用 PDB 來存放 .exe 檔或 .dll 檔的偵錯資訊。  程式的 PDB 既是輸出檔也是輸入檔，因為 LINK 在重建程式時會更新 PDB。  
  
## 請參閱  
 [LINK 輸入檔](../../build/reference/link-input-files.md)   
 [連結器選項](../../build/reference/linker-options.md)