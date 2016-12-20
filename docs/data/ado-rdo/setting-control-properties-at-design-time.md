---
title: "在設計階段設定控制項屬性 | Microsoft Docs"
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
  - "ActiveX 控制項 [C++], 屬性"
ms.assetid: 963bf498-d371-4cfd-8bed-865427dcfad9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 在設計階段設定控制項屬性
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

控制項的屬性可經由對話方塊編輯器在設計階段中設定。  當您設定屬性時，資源編輯器會以指定值初始化該控制項。  屬性仍可以程式化地變更。  
  
 在所有[資料繫結控制項](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)中找到的 **DataSource** 屬性，都可讓您指定要繫結的[資料來源](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)控制項。  
  
 繫結簡單繫結 \(Simple\-Bound\) ADO 資料繫結控制項至 ADO 資料控制項 \(ADODC\) 時，您必須將 **DataField** 屬性設成資料列集 \(Rowset\) 內的有效欄位，為控制項與資料行建立關聯。  否則，編譯的應用程式會在執行的偵錯組建中顯示判斷提示 \(Assert\) \(該判斷提示只會標記該控制項已繫結至 null 資料行\)。  
  
> [!NOTE]
>  \[一般\] 屬性索引標籤可讓您指定控制識別項 \(Control Identifier\) 和 .rc 檔所需的其他屬性 \(.rc 檔會在之後編譯，產生 Windows 程式的資源程式碼\)。  
  
### 若要在全部索引標籤內設定屬性  
  
1.  [插入 ActiveX 控制項](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md)至對話方塊中。  
  
2.  在對話方塊編輯器的控制項上按一下滑鼠右鍵，然後按一下 \[**屬性**\]。  
  
3.  按一下 \[**全部**\] 索引標籤來顯示控制項的屬性。  請為指定屬性輸入初始值。  
  
 若要在執行階段時設定控制項屬性，請參閱[修改控制項的執行階段行為](../../data/ado-rdo/modifying-a-control-s-run-time-behavior.md)。  
  
## 請參閱  
 [使用 ActiveX 控制項](../../data/ado-rdo/using-activex-controls.md)