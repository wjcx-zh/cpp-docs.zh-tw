---
title: "加入資源對話方塊 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.editors.insertresource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "資源 [Visual Studio], 加入"
  - "加入資源對話方塊"
ms.assetid: e9fb6967-738f-47e8-ab58-728cf35b3af0
caps.latest.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 12
---
# 加入資源對話方塊
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用這個對話方塊將資源加入至 C\+\+ Windows 桌面應用程式專案。  
  
> [!NOTE]
>  這項資訊不適用於 Windows 市集應用程式的資源。 如需詳細資訊，請參閱[定義應用程式資源](http://msdn.microsoft.com/zh-tw/476ea844-632c-4467-9ce3-966be1350dd4)。  
  
 **資源類型**  
 指定您想要建立的資源種類。  
  
 您可以展開資料指標和對話方塊資源類別來顯示其他資源。 這些資源位於 ...\\Microsoft Visual Studio `版本`\\VC\\VCResourceTemplates\\\<LCID\>\\mfc.rct。 如果您加入 .rct 檔案，務必將它們放置在這個目錄中，否則必須為它們指定 [Include 路徑](../windows/how-to-specify-include-directories-for-resources.md)。 如此，那些檔案中的資源將會顯示在適當分類底下的第二層。 您可以加入的 .rct 檔案數目沒有任何預設限制。  
  
 樹狀目錄控制項最上層所顯示的資源，是 Visual Studio 所提供的預設資源。  
  
 **新增**  
 根據您在 \[資源類型\] 方塊中所選取的類型來建立資源。 資源會在適當的編輯器中開啟。 例如，如果您建立對話方塊資源，它將在[對話方塊編輯器](../mfc/dialog-editor.md)中開啟。  
  
 **匯入**  
 開啟 \[匯入\] 對話方塊，您可在其中巡覽至您想匯入到目前專案的資源。 您可以匯入點陣圖、圖示、游標、HTML 資源檔、音效 \(.WAV\) 資源檔或自訂資源檔。  
  
 **自訂**  
 開啟[&#91;新增自訂資源&#93; 對話方塊](../windows/new-custom-resource-dialog-box.md)，您可在其中建立自訂資源。 自訂資源只能在二進位編輯器中編輯。  
  
## 需求  
 無  
  
## 請參閱  
 [How to: Create a Resource](../windows/how-to-create-a-resource.md)