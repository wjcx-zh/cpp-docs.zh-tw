---
title: "載入時，我應該使用何項最佳化技術來改善用戶端應用程式的效能？ | Microsoft Docs"
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
  - "DLL [C++], 最佳化"
  - "最佳化 [C++], DLL"
  - "效能 [C++], DLL"
ms.assetid: 2f8bbfb5-08b9-4a35-8302-25a1966881b1
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 載入時，我應該使用何項最佳化技術來改善用戶端應用程式的效能？
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

如果您的 DLL 是靜態連結至 MFC 的 DLL，那麼將其變更為動態連結至 MFC 的標準 DLL 會讓檔案大小變得比較小。  
  
 如果 DLL 有大量的匯出函式，請使用 .def 檔來匯出函式 \(而不是使用 **\_\_declspec\(dllexport\)**\)，並且在每個匯出函式上使用 .def 檔案 [NONAME 屬性](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md)。  NONAME 屬性會造成只有序數值，而沒有函式名稱儲存在 DLL 的匯出表，這會減少檔案的大小。  
  
 應用程式會在載入時載入隱含地連結至應用程式的 DLL。  若要改善載入效能，請嘗試將 DLL 分割成不同的 DLL。  載入一個 DLL 之後，立即置入呼叫應用程式時所需的全部函式，並且讓呼叫應用程式隱含地連結至此 DLL。  將其他呼叫應用程式時不會立刻需要的函式置於另一個 DLL，並且讓應用程式明確地連結至此 DLL。  如需詳細資訊，請參閱[決定要使用哪一個連結方法](../build/determining-which-linking-method-to-use.md)。  
  
## 請參閱  
 [DLL 常見問題集](../build/dll-frequently-asked-questions.md)