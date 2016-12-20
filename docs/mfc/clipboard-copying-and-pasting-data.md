---
title: "剪貼簿：複製和貼上資料 | Microsoft Docs"
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
  - "剪貼簿, 複製資料至"
  - "剪貼簿, 貼上"
ms.assetid: 580e10be-241f-4f9f-94cf-8302edc5beef
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 剪貼簿：複製和貼上資料
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題說明實作複製到剪貼簿並貼至您的 OLE 應用程式所需的最低工作。  建議您在進行前先閱讀 [資料物件和資料來源 \(Object Linking and Embedding，OLE\)](../mfc/data-objects-and-data-sources-ole.md) 主題。  
  
 在您可以實作複製或貼上之前，必須先在編輯功能表提供函式處理複製、剪下和貼上選項。  
  
##  <a name="_core_copying_or_cutting_data"></a> 複製或剪下資料  
  
#### 若要將資料複製到剪貼簿  
  
1.  判斷複製的資料是否為原生資料或是內嵌或連結的項目。  
  
    -   如果資料為內嵌資料或連接，請取得對選取的 `COleClientItem` 物件的指標。  
  
    -   如果資料是原生的，而且應用程式是伺服器，請建立包含選取資料衍生自 `COleServerItem` 的新物件。  否則，請建立資料的 `COleDataSource` 物件。  
  
2.  呼叫選取之項目的 `CopyToClipboard` 成員函式。  
  
3.  如果使用者選取了剪下作業而不是複製作業，請刪除應用程式的選取資料。  
  
 若要查看這個序列的範例，請參閱 MFC OLE 範例程式 [OCLIENT](../top/visual-cpp-samples.md) 和 [HIERSVR](../top/visual-cpp-samples.md) 中的 **OnEditCut** 和 **OnEditCopy** 函式。  請注意這些範例維護指標目前所選的資料，因此，第 1 步驟已完成。  
  
##  <a name="_core_pasting_data"></a> 貼上資料  
 貼上資料比複製它複雜，因為您在貼上需要選取將資料貼入應用程式的格式。  
  
#### 若要從剪貼簿貼上資料  
  
1.  在您的檢視類別，實作 **OnEditPaste** 處理使用者從\[編輯\]功能表選取粘貼選項。  
  
2.  在 **OnEditPaste** 函式中，建立 `COleDataObject` 物件並呼叫它的 `AttachClipboard` 成員函式連接至資料的這個物件在剪貼簿上。  
  
3.  呼叫 `COleDataObject::IsDataAvailable` 檢查特定格式是否可用。  
  
     或者，您可以使用 `COleDataObject::BeginEnumFormats` 尋找其他格式，直到您發現最適合您的應用程式。  
  
4.  執行格式的貼上  
  
 如需這個範例的運作方式，請參閱 **OnEditPaste** 成員函式在 MFC OLE 範例程式 [OCLIENT](../top/visual-cpp-samples.md) 和 [HIERSVR](../top/visual-cpp-samples.md) 定義的檢視類別。  
  
> [!TIP]
>  分隔貼上作業至他自己的函式的主要優點為相同的貼上程式碼可以在您的應用程式中的拖放作業期間使用。  如同在 OCLIENT 和 HIERSVR 中，您的 `OnDrop` 函式也可以呼叫 **DoPasteItem**，重複使用用來實作貼上作業的程式碼。  
  
 若要處理在編輯功能表的貼上特殊選項，請參閱 [在 OLE 的對話方塊](../mfc/dialog-boxes-in-ole.md)主題。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [加入其他格式](../mfc/clipboard-adding-other-formats.md)  
  
-   [OLE 資料物件和資料來源以及一致的資料傳輸。](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [OLE 拖放](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## 請參閱  
 [剪貼簿：使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)