---
title: "多執行緒應用程式可以存取不同執行緒中的 MFC DLL 嗎？ | Microsoft Docs"
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
  - "DLL [C++], 多執行緒"
  - "MFC DLL [C++], 多執行緒"
  - "多執行緒 [C++], DLL"
  - "執行緒 [MFC], DLL"
ms.assetid: e3452e62-021e-4d23-9cce-cff41eb8b46b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 多執行緒應用程式可以存取不同執行緒中的 MFC DLL 嗎？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

多執行緒應用程式可以存取動態連結至 MFC 的標準 DLL、和不同執行緒的擴充 DLL。  而在 Visual C\+\+ 4.2 版中，應用程式可以從應用程式所建立的多個執行緒存取靜態連結至 MFC 的標準 DLL。  
  
 4.2 之前的版本中，只有一個外部執行緒可以連結至靜態連結至 MFC 的標準 DLL。  如需從多個執行緒存取靜態連結至 MFC 的標準 DLL 的詳細資料 \(Visual C\+\+ 4.2 版之前\)，請參閱知識庫文件＜Multiple Threads and MFC \_USRDLLs＞\(Q122676\)。  
  
 請注意，Visual C\+\+ 文件裡不再使用 USRDLL 詞彙。  靜態連結至 MFC 的標準 DLL 與之前的 USRDLL 有相同的特性。  
  
## 請參閱  
 [DLL 常見問題集](../build/dll-frequently-asked-questions.md)