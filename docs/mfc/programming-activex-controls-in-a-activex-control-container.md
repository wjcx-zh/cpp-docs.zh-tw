---
title: "ActiveX 控制項容器：在 ActiveX 控制項容器中程式設計 ActiveX 控制項 | Microsoft Docs"
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
  - "ActiveX 控制項容器 [C++], 存取 ActiveX 控制項"
  - "ActiveX 控制項容器 [C++], 包裝函式類別"
  - "ActiveX 控制項 [C++], 存取"
  - "ActiveX 控制項 [C++], 包裝函式類別"
  - "確認類別對話方塊"
  - "標頭檔 [C++], ActiveX 控制項包裝函式類別的"
  - "MFC ActiveX 控制項 [C++], 在容器中存取"
  - "包裝函式類別 [C++], ActiveX 控制項"
  - "包裝函式類別 [C++], 使用"
ms.assetid: ef9b2480-92d6-4191-b16e-8055c4fd7b73
caps.latest.revision: 8
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ActiveX 控制項容器：在 ActiveX 控制項容器中程式設計 ActiveX 控制項
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

本文說明存取公開的內嵌 ActiveX 控制項的 [方法](../mfc/mfc-activex-controls-methods.md) 和 [屬性](../mfc/mfc-activex-controls-properties.md) 處理序。  基本上，您將執行下列步驟:  
  
1.  用來繪製廊的[插入 ActiveX 控制項的 ActiveX 容器專案](../mfc/inserting-a-control-into-a-control-container-application.md) 。  
  
2.  [定義 10% 成員變數](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) \(或存取其他表單\) 型別和 ActiveX 控制項包裝函式類別相同。  
  
3.  使用預先定義的包裝函式類別的成員函式的[將 ActiveX 控制項](#_core_programming_the_activex_control) 。  
  
 對於這個討論，假設您建立一個對話方塊架構的專案 \(名為 Container\) 有 ActiveX 控制項支援。  Circ 範例控制項， Circ，將加入至產生的專案。  
  
 一旦 Circ 控制插入專案 \(步驟 1\)，則會插入 Circ 控制執行個體應用程式的主對話方塊。  
  
## 程序  
  
#### 將 Circ 控制項加入至對話方塊範本  
  
1.  裝載 ActiveX 控制項容器專案。  對於這個範例，請使用 `Container` 專案。  
  
2.  按一下 \[資源檢視\] 索引標籤，  
  
3.  開啟 **Dialog** 資料夾。  
  
4.  按兩下主對話方塊範本。  對於這個範例，請使用 **IDD\_CONTAINER\_DIALOG**。  
  
5.  按一下 Circ 控制要顯示在工具箱中。  
  
6.  按一下對話方塊內的一個位置插入 Circ 控制。  
  
7.  在檔案功能表上，選取 **Save All** 儲存對話方塊範本的任何修改。  
  
## 在專案中修改  
 若要啟用容器應用程式存取 Circ 控制， Visual C\+\+ 會自動將包裝函式類別 \(`CCirc`\) 實作檔 \(.CPP\) 到容器專案和包裝函式類別標頭檔 \(。H\) 對話方塊標頭檔的檔案:  
  
 [!code-cpp[NVC_MFC_AxCont#1](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_1.h)]  
  
##  <a name="_core_the_wrapper_class_header_28h29_file"></a> 包裝函式類別標頭檔 \(。H\) 檔案  
 若要取得和設定屬性 \(和叫用方法\) Circ， `CCirc` 控制項的包裝函式類別提供所有公開的方法和屬性的宣告。  在此範例中，這些宣告在 CIRC.H. 中找到。  下列範例會定義 ActiveX 控制項公開介面類別 `CCirc` 的部分:  
  
 [!code-cpp[NVC_MFC_AxCont#2](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_2.h)]  
[!code-cpp[NVC_MFC_AxCont#3](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_3.h)]  
  
 使用標準 C\+\+ 語法，這些函式可以從其他應用程式的程序會呼叫。  如需使用這個成員函式集的相關資訊存取控制項的方法和屬性，請參閱 [將 ActiveX 控制項](#_core_programming_the_activex_control)一節。  
  
##  <a name="_core_member_variable_modifications_to_the_project"></a> 對專案的成員變數修改  
 一旦 ActiveX 控制項在對話方塊容器加入至專案並內嵌了，它可以由專案的其他組件存取。  存取控制是對話方塊類別的 [建立成員變數](../mfc/activex-control-containers-connecting-an-activex-control-to-a-member-variable.md) ， `CContainerDlg` \(步驟 2\)，與包裝函式類別相同專案中加入由 Visual C\+\+。  您可以使用成員變數隨時存取內嵌控制項。  
  
 當 **Add Member Variable** 對話方塊加入 `m_circctl` 成員變數加入至專案時，也會將下列行加入至標頭檔。 `CContainerDlg` 類別的 H\):  
  
 [!code-cpp[NVC_MFC_AxCont#4](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_4.h)]  
[!code-cpp[NVC_MFC_AxCont#5](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_5.h)]  
  
 此外，對 **DDX\_Control** 的呼叫會自動加入至 `DoDataExchange`的 `CContainerDlg` 實作:  
  
 [!code-cpp[NVC_MFC_AxCont#6](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_6.cpp)]  
  
##  <a name="_core_programming_the_activex_control"></a> 將 ActiveX 控制項  
 此時，您已經插入 ActiveX 控制項加入至對話方塊範本並建立其 10% 成員變數。  您現在可以使用一般的 C\+\+ 語法存取內嵌控制項的屬性和方法。  
  
 為明顯 \( [包裝函式類別標頭檔 \(。H\) 檔案](#_core_the_wrapper_class_header_28h29_file)\)，標頭檔 \(。 `CCirc` 包裝函式類別的 H\)，在這種情況下， CIRC.H 包含成員清單函式可用來取得和設定所有公開的屬性值。  公開方法的成員函式也可以。  
  
 修改控制項的屬性的常見位在主對話方塊類別的 `OnInitDialog` 成員函式。  呼叫這個函式，在對話方塊出現並使用初始化其內容之前，包括它的任何控制項。  
  
 下列程式碼範例會使用 `m_circctl` 成員變數修改內嵌 Circ 控制項的標題和 CircleShape 屬性:  
  
 [!code-cpp[NVC_MFC_AxCont#7](../mfc/codesnippet/CPP/programming-activex-controls-in-a-activex-control-container_7.cpp)]  
  
## 請參閱  
 [ActiveX 控制項容器](../mfc/activex-control-containers.md)