---
title: "剪貼簿：加入其他格式 | Microsoft Docs"
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
  - "剪貼簿, 格式"
  - "自訂剪貼簿資料格式"
  - "自訂格式"
  - "自訂格式, 放置在剪貼簿上"
  - "格式 [C++], 剪貼簿"
  - "註冊自訂剪貼簿資料格式"
ms.assetid: aea58159-65ed-4385-aeaa-3d9d5281903b
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 剪貼簿：加入其他格式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本主題說明如何擴充支援格式清單，特別是 OLE 支援。  主題 [剪貼簿:複製並貼上資料](../mfc/clipboard-copying-and-pasting-data.md) 描述複製和貼上剪貼簿的最低實作支援。  如果這是您所有實作，在剪貼簿上的唯一的格式為 `CF_METAFILEPICT`、、 **CF\_OBJECTDESCRIPTOR**和 **CF\_EMBEDSOURCE**，也可能是 `CF_LINKSOURCE`。  大部分的應用程式在剪貼簿需要比這三個更多格式。  
  
##  <a name="_core_registering_custom_formats"></a> 註冊自訂格式  
 若要建立自訂的格式，請依照您使用的同一個程序註冊任何自訂剪貼簿格式:傳遞格式名稱至 **RegisterClipboardFormat** 函式並使用它的傳回值做為格式識別碼 .  
  
##  <a name="_core_placing_formats_on_the_clipboard"></a> 將格式置於剪貼簿  
 若要加入更多的格式至剪貼簿上的項目，您必須覆寫您從 `COleClientItem` 或 `COleServerItem` 衍生之類別的 `OnGetClipboardData` 函式 \(根據複製的資料是否原生\)。  在這個函式，您應該使用下列程序。  
  
#### 將格式置於剪貼簿  
  
1.  建立 `COleDataSource` 物件。  
  
2.  藉由呼叫 `COleDataSource::CacheGlobalData` 將資料來源傳送至加入您的原生資料格式至支援的格式清單的函式。  
  
3.  藉由呼叫您要支援的每個標準格式的 `COleDataSource::CacheGlobalData` 加入標準格式。  
  
 這項技術用於 MFC OLE 範例程式 [HIERSVR](../top/visual-cpp-samples.md) \(請檢查 **CServerItem** 類別的 `OnGetClipboardData` 成員函式\)。  在這個範例的唯一差別在於第三個步驟不會實作，因為 HIERSVR 沒有支援其他標準格式。  
  
### 您還想知道關於哪些方面的詳細資訊？  
  
-   [OLE 資料物件和資料來源以及一致的資料傳輸。](../mfc/data-objects-and-data-sources-ole.md)  
  
-   [OLE 拖放](../mfc/drag-and-drop-ole.md)  
  
-   [OLE](../mfc/ole-background.md)  
  
## 請參閱  
 [剪貼簿：使用 OLE 剪貼簿機制](../mfc/clipboard-using-the-ole-clipboard-mechanism.md)