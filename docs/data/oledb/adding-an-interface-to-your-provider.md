---
title: "將介面加入至提供者 | Microsoft Docs"
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
  - "OLE DB 提供者樣板, 物件介面"
ms.assetid: b0fc7cf8-428a-4584-9d64-ce9074d0eb66
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 將介面加入至提供者
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

決定您要加入至介面的物件 \(通常是資料來源、資料列集、命令，或 OLE DB 提供者精靈建立的工作階段物件\)。  需要加入至介面的物件可能是提供者目前不支援的物件。  如果發生這種情形，請執行 ATL OLE DB 提供者精靈建立該物件。  對類別檢視的專案上按一下滑鼠右鍵，再按一下 \[加入\] 功能表中的 \[加入類別\]，然後按一下 \[ATL OLE DB 提供者\]。  您可將介面程式碼放在不同的目錄中，接著再將檔案複製到提供者專案中。  
  
 如果您已建立新的類別來支援該介面，請讓物件繼承自該類別。  例如，您可將 **IRowsetIndexImpl** 類別加入資料列集物件內：  
  
```  
template <class Creator>  
class CAgentRowset :   
public CRowsetImpl< CAgentRowset<Creator>, CAgentMan, Creator>,  
   public IRowsetIndexImpl< ... >   
```  
  
 使用 COM\_INTERFACE\_ENTRY 巨集將介面加入至物件內的 **COM\_MAP**。  如果沒有對應，則建立一個。  例如：  
  
```  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
END_COM_MAP()  
```  
  
 針對資料列集 \(Rowset\) 物件，請鏈結父物件的對應，以便委派物件至父類別。  在此範例中，是將 COM\_INTERFACE\_ENTRY\_CHAIN 巨集加入至對應：  
  
```  
BEGIN_COM_MAP(CAgentRowset)  
     COM_INTERFACE_ENTRY(IRowsetIndex)  
     COM_INTERFACE_ENTRY_CHAIN(CRowsetImpl)  
END_COM_MAP()  
```  
  
## 請參閱  
 [使用 OLE DB 提供者樣板](../../data/oledb/working-with-ole-db-provider-templates.md)