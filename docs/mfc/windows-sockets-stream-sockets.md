---
title: "Windows Sockets： 資料流通訊端 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Windows Sockets [MFC], stream sockets
- sockets [MFC], stream sockets
- stream sockets [MFC]
ms.assetid: 31faaa34-a995-493f-a30b-b8115293d619
caps.latest.revision: "12"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: bc112bd3cfbf1194a2898afecb513edcbc456747
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="windows-sockets-stream-sockets"></a>Windows Sockets：資料流通訊端
本文說明資料流通訊端 (其中一種可以使用的 Windows Socket 類型)。 (另一種是[資料包通訊端](../mfc/windows-sockets-datagram-sockets.md)。)  
  
 資料流通訊端提供不含記錄界限的資料流：可以是雙向的位元組資料流 (應用程式是全雙工的：它可以透過通訊端進行傳送和接收)。 資料流可以是循序傳送的不重複的資料。 (「循序」表示封包會依傳送的順序傳送。 「不重複」是指您一次只能取得一個特定封包)。其中保證會收到資料流訊息的回應，因此資料流相當適合處理大量的資料。  
  
 網路傳輸層可能會將資料拆開或分組為適當大小的封包。 `CSocket` 類別會為您處理封裝和解除封裝的步驟。  
  
 資料流採用明確的連線：通訊端 A 要求與通訊端 B 進行連線，通訊端 B 接受或拒絕連線要求。  
  
 撥打電話可以做為資料流的範例。 在一般情況下，接收的一方會依您所說出的順序聽到所說的內容，而不會重複或遺失。 例如，若要實作檔案傳輸通訊協定 (FTP)，其中會傳送任意大小的 ASCII 或二進位檔案，則可以使用資料流通訊端。  
  
 當必須確定資料抵達且當資料大小很大時，使用資料流通訊端會比使用資料包通訊端更好。 如需資料流通訊端的詳細資訊，請參閱 Windows Sockets 規格。 使用 Windows SDK 中的規格。  
  
 使用資料流通訊端可能會優於設計為使用資料包通訊端廣播給網路上所有接收通訊端的應用程式，因為  
  
-   廣播模型受限於網路氾濫 (或「風暴」) 的問題。  
  
-   之後採用的主從模型會比較有效率。  
  
-   資料流模型提供可靠的資輸，而資料包模型則沒有。  
  
-   最終的模型是採用 Unicode 和 ANSI 通訊端應用程式間的通訊能力，將 CArchive 類別提供給 CSocket 類別使用。  
  
    > [!NOTE]
    >  如果您使用 `CSocket` 類別，則必須使用資料流。 MFC 判斷提示失敗時，如果您將通訊端類型指定為**SOCK_DGRAM**。  
  
## <a name="see-also"></a>請參閱  
 [MFC 中的 Windows Sockets](../mfc/windows-sockets-in-mfc.md)   
 [Windows Sockets：背景](../mfc/windows-sockets-background.md)

