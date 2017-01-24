---
title: "引出程式庫成員 | Microsoft Docs"
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
  - "Lib"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/EXTRACT 程式庫管理員選項"
  - "EXTRACT 程式庫管理員選項"
  - "-EXTRACT 程式庫管理員選項"
  - "引出程式庫成員"
  - "LIB [C++], 引出程式庫成員"
  - "程式庫, 引出成員"
ms.assetid: a2c5c2a1-9b7e-489a-a9a4-1dec694e1fc5
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 引出程式庫成員
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以使用 LIB 來建立包含現有程式庫成員複本的目的檔 \(.obj\)。  若要引出成員複本，請使用下列語法：  
  
```  
LIB library /EXTRACT:member /OUT:objectfile  
```  
  
 這個命令會建立稱為 *objectfile* 的 .obj 檔案，包含 *library* 的 `member` 複本。  `member` 名稱是區分大小寫的。  在單一命令中您只能引出一個成員。  同時需要指定 \/OUT 選項；這並沒有預設的輸出名稱。  如果在指定的目錄 \(或是目前的目錄，如果沒有用 *objectfile* 指定目錄\) 已經有稱為 *objectfile* 的檔案，抽取出來的 *objectfile* 會取代現有檔案。  
  
## 請參閱  
 [LIB 參考](../../build/reference/lib-reference.md)