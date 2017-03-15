---
title: "支援 OLE DB 中的異動 | Microsoft Docs"
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
  - "資料庫 [C++], 異動"
  - "分散式異動 [C++]"
  - "巢狀異動 [C++]"
  - "OLE DB [C++], 異動支援"
  - "OLE DB 消費者樣板 [C++], 異動支援"
  - "異動 [C++], OLE DB 支援"
ms.assetid: 3d72e583-ad38-42ff-8f11-e2166d60a5a7
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 支援 OLE DB 中的異動
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

[交易](../../data/transactions-mfc-data-access.md)是對資料來源分組或批次一系列更新的方法，如此使得所有更新可以一次完成，或者 \(其中任何一個交易失敗時\) 在您復原交易時，不完成任何更新。  這個處理可以確保資料來源結果的完整性。  
  
 OLE DB 可以用下列三種方法支援交易：  
  
-   [\<caps:sentence id\="tgt4" sentenceid\="0699a86bb6d6316bff035b804a56f0aa" class\="tgtSentence"\>ITransactionLocal::StartTransaction\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms709786.aspx)  
  
-   [\<caps:sentence id\="tgt5" sentenceid\="39299b0fea086b86052550bd165334f7" class\="tgtSentence"\>ITransaction::Commit\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms713008.aspx)  
  
-   [\<caps:sentence id\="tgt6" sentenceid\="8e992150c28ae247d532408ca7828bfe" class\="tgtSentence"\>ITransaction::Abort\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/ms709833.aspx)  
  
## 工作階段和交易的關係  
 單一資料來源物件可以建立一個或多個工作階段物件，其中每個工作階段物件都可以在指定時間位於交易範圍之內或之外。  
  
 當工作階段沒有進入交易時，所有在資料存放區的工作階段內所做的工作會立即在每個方法呼叫上被認可\(這種模式有時稱為自動認可模式或隱含模式\)。  
  
 當工作階段進入交易時，所有在資料存放區的工作階段內所做的工作便成為交易的一部分，並會以單一單位認可或中止\(這種模式有時稱為手動認可模式\)。  
  
 交易支援是提供者專用的。  如果您正在使用的提供者可以支援交易，那麼支援 **ITransaction** 和 **ITransactionLocal** 的工作階段物件便可以進入簡單 \(即非巢狀的\) 交易。  OLE DB 樣板類別 [CSession](../../data/oledb/csession-class.md) 支援這些介面，而且是 Visual C\+\+ 建議使用的方式來實作交易支援。  
  
## 啟動和結束交易  
 您可以在消費者的資料列集物件中呼叫 `StartTransaction`、**Commit** 和 **Abort** 方法。  
  
 呼叫 **ITransactionLocal::StartTransaction** 即可啟動新本機交易。  當您啟動交易後，接續操作所完成的任何變更都要等到您認可該交易之後，才會套用到資料存放區。  
  
 呼叫 **ITransaction::Commit** 或 **ITransaction::Abort** 即可結束交易。  **Commit** 可以將交易範圍內的所有變更套用到資料存放區。  **Abort** 可以取消交易範圍內的所有變更，且將資料存放區維持在交易開始之前的狀態。  
  
## 巢狀交易  
 [巢狀交易](https://msdn.microsoft.com/en-us/library/ms716985.aspx)發生於，當某個作用中的交易已存在於工作階段中時，您又開啟了新的交易。  新交易便啟動為目前交易下的巢狀交易。  如果提供者不支援巢狀交易，則在工作階段中已存在作用中的交易時，呼叫 `StartTransaction` 即可傳回 **XACT\_E\_XTIONEXISTS**。  
  
## 分散式交易  
 分散式交易是一種更新分散式資料的交易，也就是說，資料位在一個以上的網路電腦系統上。  如果您要支援分散式系統上的交易，您應該使用 .NET Framework，而不是用 OLE DB 交易支援。  
  
## 請參閱  
 [使用存取子](../../data/oledb/using-accessors.md)