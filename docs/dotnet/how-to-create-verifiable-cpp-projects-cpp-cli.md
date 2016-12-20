---
title: "如何：建立可驗證的 C++ 專案 (C++/CLI) | Microsoft Docs"
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
  - "轉換, C++ 專案"
  - "可驗證的組件 [C++], 建立"
  - "Visual C++ 專案"
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
caps.latest.revision: 11
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 如何：建立可驗證的 C++ 專案 (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Visual C\+\+ 應用程式精靈不建立可驗證的專案，但是能將專案轉換為可驗證的。  這個主題會說明如何設定專案屬性和修改專案原始程式檔，來轉換 Visual C\+\+ 專案以產生可驗證的應用程式。  
  
## 編譯器和連結器設定  
 根據預設，.NET 專案會使用 \/clr 編譯器旗標，並將連結器設定為目標 x86 硬體。  對於可驗證的程式碼，必須使用 \/clr:safe 旗標，且必須指示連結器產生 MSIL，而不是原生機器指令。  
  
#### 若要變更編譯器和連結器設定  
  
1.  顯示專案屬性頁。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../misc/how-to-open-project-property-pages.md)。  
  
2.  在 \[**組態屬性**\] 節點下的 \[**一般**\] 頁面中，設定 \[**Common Language Runtime 支援**\] 屬性為 \[**安全 MSIL Common Language Runtime 支援 \(\/clr:safe\)**\]。  
  
3.  在 \[**連結器**\] 節點下的 \[**進階**\] 頁面中，設定 \[**CLR 映像類型**\] 屬性為 \[**強制安全 IL 影像 \(\/CLRIMAGETYPE:SAFE\)**\]。  
  
## 移除原生資料型別  
 因為原生資料型別是不可驗證的，所以即使沒有使用它們，也必須移除包含原生型別的所有標頭檔 \(Header File\)。  
  
> [!NOTE]
>  下列程序適用於 Windows Form 應用程式 \(.NET\) 和主控台應用程式 \(Console Application\) \(.NET\) 專案。  
  
#### 若要移除原生資料型別的參考  
  
1.  將 Stdafx.h 檔的所有內容標記為註解。  
  
## 設定進入點  
 因為可驗證的應用程式無法使用 C 執行階段程式庫 \(CRT\)，所以這些應用程式無法根據 CRT 呼叫主函式為標準進入點。  這表示您必須明確地提供最初要呼叫的函式名稱給連結器 \(在這種情況下，會使用 Main\(\) 而不是使用 main\(\) 或 \_tmain\(\) 來表示非 CRT 進入點，但是因為必須明確地指定進入點，因此這個名稱會是任意的\)。  
  
> [!NOTE]
>  下列程序適用於主控台應用程式 \(.NET\) 專案。  
  
#### 若要設定進入點  
  
1.  在專案的主要 .cpp 檔案中，將 \_tmain\(\) 變更為 Main\(\)。  
  
2.  顯示專案屬性頁。  如需詳細資訊，請參閱[如何：開啟專案屬性頁](../misc/how-to-open-project-property-pages.md)。  
  
3.  在 \[**連結器**\] 節點下的 \[**進階**\] 頁面中，輸入 `Main` 做為 \[**進入點**\] 屬性值。  
  
## 請參閱  
 [純粹的和可驗證的程式碼](../dotnet/pure-and-verifiable-code-cpp-cli.md)