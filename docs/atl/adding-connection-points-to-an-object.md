---
title: "Adding Connection Points to an Object | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "連接點 [C++], 加入至 ATL 物件"
  - "Implement Connection Point ATL wizard"
ms.assetid: 843531be-4a36-4db0-9d54-e029b1a72a8b
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Adding Connection Points to an Object
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

[ATL 教學課程](../atl/active-template-library-atl-tutorial.md) 示範如何建立控制項以支援連接點時，如何將事件，以及如何實作連接點。  ATL 所 [IConnectionPointImpl](../atl/reference/iconnectionpointimpl-class.md) 類別的實作連接點。  
  
 若要實作連接點，您有兩個選擇:  
  
-   藉由將物件加入至控制項或物件的連接點實作您輸出的事件來源。  
  
-   重複使用在另一個型別定義的連接點介面程式庫。  
  
 在任何情況下，實作連接點精靈使用型別程式庫完成其工作。  
  
### 將物件加入至控制項的連接點或物件。  
  
1.  在 .idl 檔案中定義的程式庫區塊的分派介面。  如果您啟用支援連接點，當您使用 ATL 控制項精靈的控制項， dispinterface 已經建立。  如果您未啟用支援連接點，當您建立控制項，您必須手動加入分配介面加入至 .idl 檔。  以下是分配介面 \(Dispinterface\) 的範例。  不需要輸出介面是分派介面，但是大部分的指令碼語言 \(例如 JScript 和 VBScript 需要，因此，這個範例會使用兩個介面:  
  
     [!code-cpp[NVC_ATL_Windowing#81](../atl/codesnippet/CPP/adding-connection-points-to-an-object_1.idl)]  
  
     使用這個 uuidgen.exe guidgen.exe 或公用程式產生 GUID。  
  
2.  加入分配介面 \(Dispinterface\)， Coclass 的 `[default,source]` 介面在專案的 .idl 檔的物件。  同樣地，因此，如果您啟用支援連接點，當您建立控制項， ATL 控制項精靈來建立 `[default,source`\] 項目。  手動加入這個項目，將以粗體顯示的程式碼行:  
  
     [!code-cpp[NVC_ATL_Windowing#82](../atl/codesnippet/CPP/adding-connection-points-to-an-object_2.idl)]  
  
     如需範例查看 [Circ](../top/visual-cpp-samples.md) ATL 範例的 .idl 檔案。  
  
3.  使用類別檢視加入方法和屬性加入至事件介面。  以滑鼠右鍵按一下類別在類別檢視中，指向捷徑功能表上的 **新增** ，然後按一下 **新增Connection Point**。  
  
4.  在實作連接點精靈的 **Source Interfaces** 清單方塊中，選取 **Project's interfaces**。  如果您選取之控制項的介面並按 **確定**，您將會:  
  
    -   產生具有實作程式碼將對事件的傳出呼叫事件的 Proxy 類別的標頭檔。  
  
    -   將項目加入至連接點對應。  
  
     您也會看見所有清單在您電腦上的型別程式庫。  您應該只使用其中一個其他型別程式庫定義自己的連接點是否要實作實際在其他型別上找到的相同輸出介面程式庫。  
  
### 重複使用在另一個型別定義的連接點介面程式庫  
  
1.  在 \[類別檢視\] 中，以滑鼠右鍵按一下實作 **BEGIN\_COM\_MAP** 巨集的類別，並在捷徑功能表上的 **新增** ，然後按一下 **新增Connection Point**。  
  
2.  在實作連接點精靈，請在型別程式庫中的型別程式庫和介面並按一下 **新增**。  
  
3.  編輯 .idl 檔為:  
  
    -   複製分配介面從使用事件來源的物件的 .idl 檔案。  
  
    -   使用在該型別程式庫的 **importlib** 指令。  
  
## 請參閱  
 [連接點](../atl/atl-connection-points.md)