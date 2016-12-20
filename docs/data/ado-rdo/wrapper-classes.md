---
title: "包裝函式類別 | Microsoft Docs"
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
  - "ActiveX 控制項 [C++], 包裝函式類別"
  - "資料繫結 [C++], ActiveX 控制項"
  - "包裝函式類別 [C++], ActiveX 控制項"
ms.assetid: ebbc17b9-cc1b-4c29-afa9-da7f9511876e
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 包裝函式類別
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當您[插入控制項](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md)至 Visual C\+\+ 專案時，根據預設並不會包含該控制項的包裝函式類別。  不過，若要[修改控制項的行為](../../data/ado-rdo/modifying-a-control-s-run-time-behavior.md)，您可為該控制項撰寫包裝函式類別。  根據您想如何用程式設計方式來處理控制項而定，會需要撰寫一或多個控制項的包裝函式類別。  
  
 包裝函式類別可用於該控制項型別程式庫 \(.tlb\) 檔內的每個 coclass。  控制項的包裝函式類別應為該控制項的名稱前面加上字母 C。  
  
 如需包裝函式類別功能的詳細資訊，請參閱控制項基本技術的物件模型。  
  
 因為傳回值必須轉換成控制項類別，所以使用 [CWnd::GetDlgItem](../Topic/CWnd::GetDlgItem.md) 也需要包裝函式類別。  例如：  
  
```  
CDBList* pDBList = 0;  
pDBList = static_cast<CDBList*>(GetDlgItem(IDC_DBLIST));  
```  
  
 您可以讀取產生的 .idl 檔，決定控制項所顯露的屬性、方法和事件，並直接檢視方法和存取子函式宣告。  您可以使用 [OLE\/COM 物件檢視器](../../data/ado-rdo/using-the-ole-com-object-viewer.md)從控制項取得其他資訊。  
  
## 請參閱  
 [使用 ActiveX 控制項](../../data/ado-rdo/using-activex-controls.md)   
 [修改控制項的執行階段行為](../../data/ado-rdo/modifying-a-control-s-run-time-behavior.md)