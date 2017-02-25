---
title: "在提供者內設定屬性 | Microsoft Docs"
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
  - "OLE DB 提供者, 屬性"
  - "屬性 [C++], OLE DB 提供者"
ms.assetid: 26a8b493-7ec4-4686-96d0-9ad5d2bca5ac
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 在提供者內設定屬性
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

為您要的屬性尋找屬性群組和屬性 ID。  如需詳細資訊，請參閱《OLE DB 程式設計人員參考》中的 [OLE DB 屬性](https://msdn.microsoft.com/en-us/library/ms722734.aspx)。  
  
 在由精靈產生的提供者程式碼中，尋找對應至屬性群組的屬性對應   屬性群組的名稱通常都對應至物件的名稱。  命令和資料列集屬性可在命令或資料列集內找到，資料來源和初始化屬性可在資料來源物件內找到。  
  
 在屬性對應內加入 [PROPERTY\_INFO\_ENTRY\_EX](../../data/oledb/property-info-entry-ex.md) 巨集。  PROPERTY\_INFO\_ENTRY\_EX 需要四個參數：  
  
-   對應至您的屬性的屬性 ID。  您必須移除屬性名稱前面的 7 個字元 \("DBPROP\_"\)。  例如，如果您想加入 **DBPROP\_MAXROWS**，就將 `MAXROWS` 當做第一個項目來傳遞。  如果這是一個自訂屬性，便需傳遞完整的 GUID 名稱 \(例如，`DBMYPROP_MYPROPERTY`\)。  
  
-   屬性的變數型別 \(《OLE DB 程式設計人員參考》中的 [OLE DB 屬性](https://msdn.microsoft.com/en-us/library/ms722734.aspx)\)。  輸入對應至資料型別的 **VT\_**  型別 \(例如 `VT_BOOL` 或 `VT_I2`\)。  
  
-   指示屬性是否可讀取、可寫入和其所屬群組的旗標。  例如，下列程式碼指示資料列集群組所屬的讀取\/寫入屬性：  
  
    ```  
    DBPROPFLAGS_ROWSET | DBPROPFLAGS_READ | DBPROPFLAGS_WRITE  
    ```  
  
-   屬性的基本數值。  例如，對布林 \(Boolean\) 型別而言可能是 **VARIANT\_FALSE**，對於整數型別而言可為零。  除非屬性變更，否則屬性就會有這個值。  
  
    > [!NOTE]
    >  有些屬性會連接或鏈結至其他屬性，例如書籤或更新。  當消費者將一個屬性設定為 True 時，可能也設定了另一個屬性。  OLE DB 提供者樣板以 [CUtlProps::OnPropertyChanged](../../data/oledb/cutlprops-onpropertychanged.md) 方法支援這種行為。  
  
## Microsoft OLE DB 提供者所忽略的屬性  
 Microsoft OLE DB 提供者忽略以下 OLE DB 屬性：  
  
-   **DBPROP\_MAXROWS** 僅適用於唯讀提供者 \(也就是說，DBPROP\_IRowsetChange 和 DBPROP\_IRowsetUpdate 是 False\)，否則將不會支援此屬性。  
  
-   忽略 **DBPROP\_MAXPENDINGROWS**，提供者指定其自身的限制。  
  
-   忽略 **DBPROP\_MAXOPENROWS**，提供者指定其自身的限制。  
  
-   忽略 **DBPROP\_CANHOLDROWS**，提供者指定其自身的限制。  
  
## 請參閱  
 [使用 OLE DB 提供者樣板](../../data/oledb/working-with-ole-db-provider-templates.md)