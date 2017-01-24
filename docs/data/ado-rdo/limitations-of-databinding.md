---
title: "資料繫結限制 | Microsoft Docs"
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
  - "資料繫結 [C++], Visual C++ 中的限制"
ms.assetid: 376d7738-5252-4caa-adda-a5486ab2a2a2
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 資料繫結限制
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

資料繫結是迅速建立資料應用程式的有效方式。  不過目前的資料繫結控制項架構原本就是兩層。  
  
## 延展性  
 ADO 資料繫結控制項只能自 ADO 資料控制項存取資料。  RDO 資料繫結控制項只能自 RDO RemoteData 控制項存取資料。  針對 RDO RemoteData 控制項而言，您只能使用雙層架構，而此架構會令資料庫伺服器直接接收所有的資料擷取要求。  若要防止直接連接至資料庫伺服器，請編寫一個提供者來允許存取中介層 \(Middle Tier\) 的商務和資料物件。  ADO 資料控制項會連接到這些物件，而不是連接到資料庫伺服器。  可在交易伺服器內 \(例如，COM\+ 1.0 服務\) 快取和管理此類中介層物件。  
  
## 版本和散發  
 發行新版的控制項時，應用程式必須以新版本來進行測試。  如果使用者電腦內安裝了另一個應用程式，並且擁有不同版本的控制項，該應用程式將會經過檢查。  最後，當新版的控制項發行時，新的控制項必須散發給應用程式的使用者。  
  
 **驅動程式和提供者**  
  
 資料繫結頂多只能提供您使用的 ODBC 驅動程式，或 OLE DB 提供者 \(Provider\) 的功能。  因為驅動程式和提供者負責顯露資料給資料控制項，請務必確認驅動程式或提供者可支援您需要的功能。  當您選取一個驅動程式或提供者之後，必須確認使用者已安裝該驅動程式或提供者。  這包括了安裝驅動程式或提供者所需的任何中介軟體。  例如，就 ODBC Oracle 連接而言，使用者不僅需安裝 ODBC Oracle 驅動程式，還需安裝 Oracle 的 SQL\*Net 中介軟體。  若要連接至 Oracle 7.3 伺服器，則建議使用 Microsoft Oracle ODBC 驅動程式。  
  
 **可程式化能力**  
  
 因為 ActiveX 控制項設計成黑箱元件，所以它的可程式化能力將僅開放給開發人員來存取控制項介面。  在資源編輯器的資料繫結模型中，這將經由插入 ActiveX 控制項精靈所產生的[包裝函式類別](../../data/ado-rdo/wrapper-classes.md)來實作。  如果精靈偵測不到 coclass，就不會產生任何包裝函式類別，也不會有任何的程式化存取。  
  
 雖然有這些限制，資料繫結仍提供一個可快速以 Visual C\+\+ 來使用原型 \(Prototype\) 資料應用程式的方式。  如果開發速度佔相當重要的考量，在設計應用程式時就該考慮資料繫結。  
  
## 請參閱  
 [在 Visual C\+\+ 中使用 ActiveX 控制項進行資料繫結](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)