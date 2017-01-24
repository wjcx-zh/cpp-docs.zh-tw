---
title: "在 Visual C++ 中使用 RDO 資料繫結 | Microsoft Docs"
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
  - "資料繫結 [C++], RDO"
  - "RDO [C++], 資料繫結"
  - "RDO RemoteData 控制項, 繫結 Visual C++ 中的資料"
  - "RemoteData 控制項, 繫結 Visual C++ 中的資料"
ms.assetid: 02b9cfe7-7bbe-4a01-b075-e28d9536ac4b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Visual C++ 中使用 RDO 資料繫結
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

若要在 Visual C\+\+ 內使用 RDO 資料繫結，您需要加入 RDO RemoteData 控制項，並指到資料來源和資料錄來源 \(SQL 查詢\)。  您也需要加入 RDO 資料繫結控制項，將它指到 RDO RemoteData 控制項，並選取要繫結至 RDO RemoteData 控制項之資料錄來源的欄位。  
  
### 若要在 Visual C\+\+ 內使用 RDO 資料繫結  
  
1.  若您尚未設定 [ODBC 資料來源](../../data/ado-rdo/odbc-connections.md)的組態，請先進行設定。  
  
2.  使用 MFC 應用程式精靈來建立 MFC 對話方塊應用程式或 MFC 表單樣式應用程式。  
  
3.  將 Microsoft RemoteData 控制項 \(RDO RemoteData 控制項\) 加至對話方塊內；請參閱[將控制項插入 Visual C\+\+ 應用程式](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md)。  
  
4.  將 RDO RemoteData 控制項指到您的 ODBC 資料來源。  
  
    1.  在控制項上按一下滑鼠右鍵，然後按一下 \[**屬性**\]。  
  
    2.  按一下 \[控制項\] 索引標籤。  
  
    3.  設定 ODBC 資料來源的 **DataSource**。  
  
    4.  視需要為 ODBC 資料來源設定使用者名稱和密碼。  如果資料來源不需要使用者名稱或密碼，請保留為空白。  
  
    5.  在 **SQL** 屬性輸入一個 SQL 查詢。  資料繫結控制項可繫結至此查詢的結果。  
  
5.  必要時設定任何其他的 RDO RemoteData 控制項屬性。  
  
6.  加入資料繫結控制項。  例如，加入 **DBGrid** 控制項，並依下列方式設定資料來源。  
  
    1.  在 DBGrid 上按一下滑鼠右鍵，然後按一下 \[**屬性**\]。  
  
    2.  按一下 \[**全部**\] 索引標籤。  
  
    3.  設定 RDO RemoteData 控制項的 **DataSource** 屬性。  按一下屬性的下拉式清單方塊，然後找出 RDO RemoteData 控制項的 ID。  預設的 ID 名稱是 IDC\_REMOTEDATACTL1。  
  
7.  若要在測試模式中執行，請使用 CTRL\+T。  您可以捲動資料。  按下 ESC 鍵或關閉對話方塊來結束測試模式。  
  
 如果您要編譯並執行程式，也可以捲動資料。  
  
## 請參閱  
 [RDO 資料繫結](../../data/ado-rdo/rdo-databinding.md)   
 [在 Visual C\+\+ 中使用 ActiveX 控制項進行資料繫結](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)