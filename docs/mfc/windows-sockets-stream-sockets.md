---
title: "Windows Sockets：資料流通訊端 | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
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
  - "通訊端 [C++], 資料流通訊端"
  - "資料流通訊端 [C++]"
  - "Windows Sockets [C++], 資料流通訊端"
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
caps.latest.revision: 12
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Windows Sockets：資料流通訊端
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明資料流通訊端，可利用兩個 Windows Sockets 的其中一種型別。\(另一個型別為 [資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)\)。  
  
 資料流通訊端提供未記錄界限的資料流:可以是雙向的位元組資料流 \(應用程式全雙工:它可以透過通訊端傳送和接收\)。  資料流可以重新排序至順序交付， unduplicated 資料。\(「依序」表示封包按傳送的順序傳遞。「無副本的」 是指您一次只能取得一個特定封包。\)資料流訊息的收據保證，和資料流相當適合處理大量的資料。  
  
 網路傳輸層可能終結或群組資料讀入封包適當的大小。  `CSocket` 類別會處理封裝並為您打開。  
  
 資料流以明確連結:通訊端的要求與通訊端 B 的連接;通訊端 B 接受或拒絕要求。  
  
 呼叫為資料流提供良好類比。  在一般情況下，這個接收的一方聽見所按順序假設您將它，不用複製或遺失。  資料流通訊端為實作是適當的，例如，例如 File Transfer Protocol \(FTP\)，協助將任意大小 ASCII 或二進位檔案。  
  
 資料流通訊端最好是對資料包通訊端，則必須確定資料抵達時，此外，當資料大小太大時。  如需資料流通訊端的詳細資訊，請參閱 Windows Sockets 規格。  這個規格可用於 [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)]。  
  
 使用資料流通訊端可以較多所設計的應用程式為廣播使用資料包通訊端到網路上的所有接收的通訊端，因為  
  
-   這個模型廣播受限於網路氾濫式 \(或「自暴」\) 問題的限制。  
  
-   隨後獲得的主從模型會更有效率。  
  
-   資料流模型提供可靠的資料時，傳送資料包模型不。  
  
-   最終模型利用通訊 Unicode 之間，並把 ANSI CArchive 分類的通訊端應用程式有一個 CSocket 分類。  
  
    > [!NOTE]
    >  如果您使用 `CSocket`類別，您必須使用資料流。  如果您指定，通訊端類型做為 **SOCK\_DGRAM**， MFC 判斷提示就會失敗。  
  
## 請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [Windows Sockets：背景](../mfc/windows-sockets-background.md)