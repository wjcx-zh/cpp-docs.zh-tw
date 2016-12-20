---
title: "在 Visual C++ 中使用 ADO 資料繫結 | Microsoft Docs"
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
  - "ADO [C++], 資料繫結"
  - "繫結控制項 [C++], ADO"
  - "繫結控制項 [C++], RDO"
  - "資料繫結 [C++], ADO"
  - "資料繫結 [C++], RDO"
ms.assetid: ad193919-3437-41ee-b41c-9d353f6274e5
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在 Visual C++ 中使用 ADO 資料繫結
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 Visual C\+\+ 使用 ADO 資料繫結時需要執行下列步驟：  
  
-   加入 ADO 資料控制項  
  
-   指向資料來源  
  
-   指定資料錄來源 \(SQL 查詢或資料擷取語言\)  
  
-   加入 ADO 資料繫結控制項  
  
-   將資料繫結控制項連接至 ADO 資料控制項  
  
-   選取要繫結至 ADO 資料控制項之資料錄來源欄位  
  
### 若要在 Visual C\+\+ 內使用 ADO 資料繫結  
  
1.  使用 MFC 應用程式精靈來建立 MFC 對話方塊應用程式或 MFC 表單樣式應用程式。  
  
2.  將 Microsoft ADO 資料控制項加入至對話方塊；如需詳細資訊，請參閱[將控制項插入 Visual C\+\+ 應用程式](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md)。  
  
3.  將 ADO 資料控制項指到 OLE DB 資料來源。  
  
    1.  在 ADO 資料控制項上按一下滑鼠右鍵，然後按一下 \[**屬性**\]。  
  
    2.  在 \[控制項\] 索引標籤內按一下 \[使用連接字串\]。  您可使用所供應的提供者，或是刪除它。  
  
    3.  按一下 \[**建置**\]。  如果刪除了 \[使用連接字串\] 內的提供者，現在可以定義一個提供者。  在定義提供者之後，可再次存取 ADO 資料控制項的屬性，然後再次選取 \[**組建**\] 繼續執行。  
  
         如果在選取 \[**組建**\] 之前已經在 \[使用連接字串\] 定義了提供者，現在便可定義資料連結屬性。  此時會出現資料連結精靈。  
  
    4.  必要時請變更 \[提供者\]，並定義適合提供者的 \[位置\] 和 \[**資料來源**\] 值。  例如，如果您使用的是 SQL Server 提供者，\[位置\] 將指定資料庫伺服器，而 \[**資料來源**\] 則會指定資料庫。  如果您是使用 ODBC 提供者，\[**資料來源**\] 會對應至 ODBC DSN。  
  
    5.  如果資料來源需要的話，請按一下 \[驗證\] 索引標籤，然後設定 \[使用者名稱\] 和 \[**密碼**\] 值。  
  
    6.  按一下 \[**連線**\] 索引標籤，然後按一下 \[測試連線\] 來測試資料來源。  捲動至結果視窗的底部，以檢視是否通過測試。  如果測試結果失敗，請檢查資料來源的組態。  常見的錯誤包括無效的密碼，以及不正確的 \[位置\] 和 \[**資料來源**\] 欄位值。  
  
    7.  結束資料連結精靈，然後返回 ADO 資料控制項的屬性工作表 \(Property Sheet\)。  
  
4.  在 `RecordSource` 索引標籤中的 \[命令文字 \(SQL\)\] 輸入查詢。  資料繫結控制項可繫結至此查詢的結果。  查詢通常是 SQL。  不過，有些 OLE DB 提供者 \(Provider\) 不是使用 SQL。  
  
5.  依照需要設定任何其他的 ADO 資料控制項屬性，並關閉該 ADO 資料控制項的屬性工作表。  
  
6.  加入資料繫結控制項。  例如，加入 DataGrid 控制項，它和 RDO DBGrid 控制項不同。  
  
7.  設定 DataGrid 的屬性。  
  
    1.  在 \[資料格\] 上按一下滑鼠右鍵，然後按一下 \[**屬性**\]。  
  
    2.  按一下 \[**全部**\] 索引標籤，並將 **DataSource** 屬性設為 ADO 資料控制項。  按一下 \[DataSource\] 下拉式清單，並找出此 ADO 資料控制項的 ID。  預設的 ID 名稱是 IDC\_ADODC1。  
  
8.  若要在測試模式中執行，請按 CTRL\+T。  您可以捲動資料。  按下 ESC 鍵或關閉對話方塊來結束測試模式。  
  
 如果您要編譯並執行程式，也可以捲動資料。  
  
## 請參閱  
 [ADO 資料繫結](../../data/ado-rdo/ado-databinding.md)   
 [在 Visual C\+\+ 中使用 ActiveX 控制項進行資料繫結](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)