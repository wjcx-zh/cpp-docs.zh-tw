---
title: "使用測試容器測試屬性和事件 | Microsoft Docs"
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
  - "ActiveX 控制項測試容器"
  - "ActiveX 控制項 [C++], 測試"
  - "偵錯 ActiveX 控制項"
  - "屬性 [MFC], 測試"
  - "測試容器"
  - "測試, 測試容器"
  - "tstcon32.exe"
ms.assetid: 626867cf-fe53-4c30-8973-55bb93ef3917
caps.latest.revision: 13
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 使用測試容器測試屬性和事件
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

測試容器應用程式在 Visual C\+\+ 中傳輸，是測試和偵錯 ActiveX 控制項的 ActiveX 控制項容器。  測試容器可讓控制項開發人員變更其屬性，叫用其方法和引發其事件測試控制項的功能。  測試容器可以顯示資料繫結通知記錄及測試的 ActiveX 控制項的永續性功能提供的功能：您可以將屬性加入至資料流或到 substorage，重新載入以及檢查儲存的資料流資料。  本節說明如何使用測試容器的基本功能。  如需詳細資訊，請在執行測試容器時選擇 **Help** 功能表。  
  
### 存取 ActiveX 控制項測試容器  
  
1.  建置 [TSTCON 範例：ActiveX 控制項測試容器](../top/visual-cpp-samples.md)。  
  
### 若要測試您的 ActiveX 控制項  
  
1.  在測試容器的 **Edit** 功能表上，按一下 **Insert New Control**。  
  
2.  在 **Insert Control** 方塊中，選取想要的控制項並按一下 \[**好**\]。  控制項會出現在控制項容器。  
  
    > [!NOTE]
    >  如果控制項在 **Insert Control** 對話方塊未列出，請確定您已使用測試容器的 **File** 功能表的 **Register Controls** 命令將它註冊。  
  
 現在您可以測試控制項的屬性或事件。  
  
#### 若要測試屬性  
  
1.  按一下 \[**控制項**\] 功能表上的 \[**叫用方法**\]。  
  
2.  在 **Method Name** 下拉式清單中，選取您要測試的屬性的 PropPut 方法。  
  
3.  修改 **Parameter Value** 或 **Parameter Type** 並按一下 **Set Value** 按鈕。  
  
4.  按一下 **Invoke**  將新值加入至物件。  
  
     屬性現在包含新的值。  
  
#### 若要測試事件和指定事件資訊的目的。  
  
1.  在 \[**工具**\] 功能表上按一下 \[**記錄**\]。  
  
2.  指定事件資訊的目的。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [如何：偵錯 ActiveX 控制項](../Topic/How%20to:%20Debug%20an%20ActiveX%20Control.md)