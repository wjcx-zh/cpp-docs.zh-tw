---
title: "建立簡單消費者 | Microsoft Docs"
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
  - "OLE DB 消費者, 建立"
ms.assetid: ae32d657-72ea-4db8-9839-75cb5cff68ae
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 建立簡單消費者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

請使用 ATL 專案精靈和 ATL OLE DB 消費者精靈產生 OLE DB 樣板消費者。  
  
#### 若要替 OLE DB 消費者建立主控台應用程式  
  
1.  在 \[**檔案**\] 功能表上，按一下 \[**新增**\]，然後按一下 \[**專案**\]。  
  
     \[**新增專案**\] 對話方塊隨即出現。  
  
2.  在 \[專案類型\] 窗格中按一下 \[**Visual C\+\+ 專案**\] 資料夾，然後在 \[樣板\] 窗格中按一下 \[**Win32 專案**\] 圖示。  在 \[名稱\] 方塊中輸入專案名稱，例如 **MyCons**。  
  
3.  按一下 \[**確定**\]。  
  
     Win32 專案精靈出現。  
  
4.  在 \[**應用程式設定**\] 頁上選取 \[主控台應用程式\]，然後選取 \[加入 ATL 的支援\]。  
  
5.  按一下 \[完成\] 關閉精靈並產生專案。  
  
 接下來，使用 ATL OLE DB 消費者精靈加入 OLE DB 消費者物件。  
  
#### 若要使用 ATL OLE DB 消費者精靈建立消費者  
  
1.  在 \[類別檢視\] 中以滑鼠右鍵按一下 `MyCons` 專案。  
  
2.  在捷徑功能表中按一下 \[加入\]，然後按一下 \[加入類別\]。  
  
     \[加入類別\] 對話方塊隨即出現。  
  
3.  按一下 \[類別\] 窗格中的 \[**Visual C\+\+**\]，然後按一下 \[範本\] 窗格中的 \[ATL OLE DB 消費者\]，再按一下 \[開啟\]。  
  
     此時會顯示 ATL OLE DB 消費者精靈。  
  
4.  按一下 \[**資料來源**\] 按鈕。  
  
     \[**資料連結屬性**\] 對話方塊隨即出現。  
  
5.  在 \[**資料連結內容**\] 對話方塊中，執行下列工作：  
  
    -   在 \[提供者\] 索引標籤上，指定一個 OLE DB 提供者。  
  
    -   在 \[**連接**\] 索引標籤上，指定伺服器名稱、資料來源的登入 ID 和密碼，以及該伺服器的資料庫。  
  
    > [!NOTE]
    >  \[**資料連結屬性**\] 對話方塊的 \[允許儲存密碼\] 功能會出現安全性的問題。  \[輸入資訊登入伺服器\] 中有兩個選項按鈕：\[使用 Windows NT 整合安全性\] 和 \[使用特定使用者名稱和密碼\]。  
  
    > [!NOTE]
    >  如果您選取 \[使用特定使用者名稱和密碼\]，可以選擇是否要儲存密碼 \(使用 \[允許儲存密碼\] 核取方塊\)；但這個選項並不安全。  建議您選取 \[使用 Windows NT 整合安全\]；這個選項使用 Windows NT 來確認您的識別。  
  
    > [!NOTE]
    >  若您無法使用 Windows NT 整合安全性，則應使用中介層 \(Middle Tier\) 的應用程式來提示使用者密碼，或是將密碼儲存在有使用安全性機制保護的位置 \(而非存在原始程式碼內\)。  
  
     選取提供者和其他設定之後，請按一下 \[測試連線\]，驗證先前對話方塊頁所做的選取。  如果 \[**結果**\] 方塊的報告為 \[`Test connection succeeded`\]，請按一下 \[**確定**\] 建立資料連結。  
  
     \[選取資料庫物件\] 對話方塊隨即出現。  
  
6.  使用樹狀結構控制項來選取資料表、檢視或預存程序 \(Stored Procedure\)。  為達成此程序的目的，請選取北風資料庫的產品資料表。  
  
7.  按一下 \[**確定**\]。  這會讓您回到 ATL OLE DB 消費者精靈。  
  
8.  精靈會根據您選取的資料表、檢視或預存程序的名稱，填寫 \[`Class`\] 和 \[**.h 檔案**\] 的名稱。  您可以視需要編輯這些名稱。  
  
9. 清除 \[屬性化\] 核取方塊，以便讓精靈使用 [OLE DB 樣板類別](../../data/oledb/ole-db-consumer-templates-reference.md)來建立消費者程式碼，而非使用預設的 [OLE DB 消費者屬性](../../windows/ole-db-consumer-attributes.md)。  
  
10. 選取 \[**型別**\] 下的 \[**命令**\]。  
  
     如果您選取 \[命令\]，精靈會建立以 [CCommand](../../data/oledb/ccommand-class.md) 為架構的消費者；如果您選取 \[資料表\]，精靈會建立以 [CTable](../../data/oledb/ctable-class.md) 為架構的消費者。  這種資料表或命令類別會根據選定物件名稱來命名，但是您可以變更名稱。  
  
11. 讓 \[支援\] 底下的 \[變更\]、\[插入\] 和 \[刪除\] 方塊處於清除狀態。  
  
     您可以視需要選擇 \[變更\]、\[插入\] 和 \[刪除\] 核取方塊以支援資料列集的資料錄之變更、插入和刪除動作。  如需將資料寫入資料存放區的詳細資訊，請參閱[更新資料列集](../../data/oledb/updating-rowsets.md)。  
  
12. 按一下 \[完成\] 以建立消費者。  
  
 精靈會產生一命令類別和使用者資料錄類別，如同[消費者精靈產生的類別](../../data/oledb/consumer-wizard-generated-classes.md)中所示。  命令類別會具有您在精靈的 \[`Class`\] 方塊中輸入的名稱 \(在此例中為 `CProducts`\)，而使用者資料錄類別的名稱則以 "*ClassName*Accessor" 格式表示 \(在此例中為 `CProductsAccessor`\)。  
  
> [!NOTE]
>  這個精靈會將下列程式碼放入 Products.h：  
  
```  
#error Security Issue: The connection string may contain a password  
```  
  
> [!NOTE]
>  這一行程式碼可以避免消費者應用程式進行編譯，並提醒您檢查硬式編碼密碼的連接字串。  在檢查連接字串之後，使可移除這行程式碼。  
  
## 請參閱  
 [使用精靈建立 OLE DB 消費者](../../data/oledb/creating-an-ole-db-consumer-using-a-wizard.md)