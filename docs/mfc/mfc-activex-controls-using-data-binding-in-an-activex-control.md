---
title: "MFC ActiveX 控制項：在 ActiveX 控制項中使用資料繫結 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "bindable"
  - "requestedit"
  - "defaultbind"
  - "displaybind"
  - "dispid"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "繫結控制項 [C++], MFC ActiveX"
  - "控制項 [MFC], 資料繫結"
  - "資料繫結 [C++], MFC ActiveX 控制項"
  - "資料繫結控制項 [C++], MFC ActiveX 控制項"
  - "MFC ActiveX 控制項, 資料繫結"
ms.assetid: 476b590a-bf2a-498a-81b7-dd476bd346f1
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# MFC ActiveX 控制項：在 ActiveX 控制項中使用資料繫結
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

其中一個 ActiveX 控制項更強大的用途是資料繫結，讓控制項屬性繫結至資料庫中的特定欄位。  當使用者修改這個繫結資料時，控制項通知資料庫並要求記錄欄位更新。  資料庫會通知要求成功的控制項或失敗。  
  
 本文將工作的控制項。  實作與資料庫中的資料繫結互動是控制項容器的責任。  如何處理在容器的資料庫互動超出這個文件的範圍之外。  如何準備資料繫結的控制項在其他說明本文。  
  
 ![資料繫結控制項的概念圖](../mfc/media/vc374v1.png "vc374V1")  
資料繫結控制項的概念圖  
  
 `COleControl` 類別提供讓資料繫結簡單流程實作的兩個成員函式。  第一個函式， [BoundPropertyRequestEdit](../Topic/COleControl::BoundPropertyRequestEdit.md)，用來要求使用權限變更屬性值。  在成功變更之後，[BoundPropertyChanged](../Topic/COleControl::BoundPropertyChanged.md)，第二個函式，呼叫屬性值。  
  
 本章節涵蓋下列主題：  
  
-   [建立 Bindable 內建屬性。](#vchowcreatingbindablestockproperty)  
  
-   [建立 Bindable Get\/Set 方法](#vchowcreatingbindablegetsetmethod)  
  
##  <a name="vchowcreatingbindablestockproperty"></a> 建立 Bindable 內建屬性。  
 建立資料繫結共用屬性，但是，雖然較可能會想要 [繫結 get\/set 方法](#vchowcreatingbindablegetsetmethod)。  
  
> [!NOTE]
>  預設為內建屬性有 **bindable** 和 **requestedit** 屬性。  
  
#### 使用加入屬性精靈，將可繫結的內建屬性。  
  
1.  使用 [MFC ActiveX 控制項精靈](../mfc/reference/mfc-activex-control-wizard.md)，啟動專案。  
  
2.  以滑鼠右鍵按一下控制項的介面節點。  
  
     這會開啟捷徑功能表。  
  
3.  從捷徑功能表中，按一下 \[**加入**\]，再按一下 \[**加入屬性**\]。  
  
4.  選取其中一個項目從 **Property Name** 下拉式清單。  例如，您可以選取 **Text**。  
  
     由於 **Text** 是內建屬性， **bindable** 和 **requestedit** 屬性已經被檢查。  
  
5.  選取下列核取方塊從 **IDL Attributes** 選項:將屬性的 **displaybind** 和 **defaultbind** 至項目的 .IDL 的屬性定義檔案。  這些屬性讓控制項顯示給使用者並將內建屬性預設可繫結屬性。  
  
 此時，您的控制項可以顯示資料來源中的資料，不過，使用者將無法更新資料欄位。  如果您想要控制項也可以更新資料，請將 `OnOcmCommand` [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) 函式如下所示:  
  
 [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
 您現在可以建立專案，將控制項註冊。  當您在對話方塊插入控制項， **Data Field** 和 \[**資料來源**\] 屬性加入了，而且您在控制項現在可以選擇資料來源和欄位顯示。  
  
##  <a name="vchowcreatingbindablegetsetmethod"></a> 建立 Bindable Get\/Set 方法  
 除了資料繫結 get\/set 方法之外，您也可以建立 [繫結的內建屬性。](#vchowcreatingbindablestockproperty)。  
  
> [!NOTE]
>  這個程序假設您有一個 ActiveX 控制項專案的子類別視窗控制項。  
  
#### 使用加入屬性精靈，將可繫結的 get\/set 方法  
  
1.  載入控制項的專案。  
  
2.  在 **Control Settings** 頁面，為控制項選取視窗類別的子類別。  例如，您可能想要子類別化編輯控制項。  
  
3.  載入控制項的專案。  
  
4.  以滑鼠右鍵按一下控制項的介面節點。  
  
     這會開啟捷徑功能表。  
  
5.  從捷徑功能表中，按一下 \[**加入**\]，再按一下 \[**加入屬性**\]。  
  
6.  在 \[**屬性名稱**\] 方塊中輸入屬性的名稱。  在這個範例中使用 `MyProp`。  
  
7.  從 \[**屬性型別**\] 下拉式清單中選取設定的資料型別。  在這個範例中使用 **short**。  
  
8.  對於 **Implementation Type**，按一下 **Get\/Set Methods**。  
  
9. 從 IDL Attributes 選項選取下列核取方塊:將屬性的 **bindable**, **requestedit**, **displaybind** 和 **defaultbind** 加入至項目的 .IDL 的屬性定義檔案。  這些屬性讓控制項顯示給使用者並將內建屬性預設可繫結屬性。  
  
10. 按一下 \[**完成**\]。  
  
11. 修改 `SetMyProp` 函式主體，讓它包含下列程式碼:  
  
     [!code-cpp[NVC_MFC_AxData#2](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_2.cpp)]  
  
12. 參數會傳遞至 `BoundPropertyChanged` 和 `BoundPropertyRequestEdit` 函式是屬性的 Dispid，為參數傳遞至屬性的 ID \(\) 屬性在 .IDL 檔案。  
  
13. 修改 [OnOcmCommand](../mfc/mfc-activex-controls-subclassing-a-windows-control.md) 函式，讓它包含下列程式碼:  
  
     [!code-cpp[NVC_MFC_AxData#1](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_1.cpp)]  
  
14. 修改 `OnDraw` 函式，使它包含下列程式碼。  
  
     [!code-cpp[NVC_MFC_AxData#3](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_3.cpp)]  
  
15. 對標頭檔的公開部分控制項類別的標頭檔，加入下列定義 \(建構函式\) 成員變數:  
  
     [!code-cpp[NVC_MFC_AxData#4](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_4.h)]  
  
16. 將下行程式碼 `DoPropExchange` 的最後一行\):  
  
     [!code-cpp[NVC_MFC_AxData#5](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_5.cpp)]  
  
17. 修改 `OnResetState` 函式，使它包含下列程式碼。  
  
     [!code-cpp[NVC_MFC_AxData#6](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_6.cpp)]  
  
18. 修改 `GetMyProp` 函式，使它包含下列程式碼。  
  
     [!code-cpp[NVC_MFC_AxData#7](../mfc/codesnippet/CPP/mfc-activex-controls-using-data-binding-in-an-activex-control_7.cpp)]  
  
 您現在可以建立專案，將控制項註冊。  當您在對話方塊插入控制項， **Data Field** 和 \[**資料來源**\] 屬性加入了，而且您在控制項現在可以選擇資料來源和欄位顯示。  
  
## 請參閱  
 [MFC ActiveX 控制項](../mfc/mfc-activex-controls.md)   
 [資料繫結控制項 \(ADO 和 RDO\)](../data/ado-rdo/data-bound-controls-ado-and-rdo.md)