---
title: "/CLRTHREADATTRIBUTE (設定 CLR 執行緒屬性) | Microsoft Docs"
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
  - "VC.Project.VCLinkerTool.CLRThreadAttribute"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/CLRTHREADATTRIBUTE 連結器選項"
  - "-CLRTHREADATTRIBUTE 連結器選項"
ms.assetid: 4907e9ef-5031-446c-aecf-0a0b32fae1e8
caps.latest.revision: 14
caps.handback.revision: 14
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /CLRTHREADATTRIBUTE (設定 CLR 執行緒屬性)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

明確指定 CLR 程式進入點的執行緒屬性。  
  
## 語法  
  
```  
/CLRTHREADATTRIBUTE:{STA|MTA|NONE}  
```  
  
#### 參數  
 MTA  
 套用 MTAThreadAttribute 屬性至程式的進入點。  
  
 NONE  
 等同於不指定 \/CLRTHREADATTRIBUTE 相同。讓 Common Language Runtime \(CLR\) 設定預設的執行緒屬性。  
  
 STA  
 套用 STAThreadAttribute 屬性至程式的進入點。  
  
## 備註  
 設定執行緒屬性只有在建置 .exe 時有效，因為它會影響主執行緒的進入點。  
  
 如果您使用預設進入點 \(例如 main 或 wmain\)，請在預設進入函式上，透過使用 \/CLRTHREADATTRIBUTE，或透過放置執行緒屬性 \(STAThreadAttribute 或 MTAThreadAttribute\)，指定執行緒模型。  
  
 如果您使用非預設進入點，請在非預設進入函式上，透過使用 \/CLRTHREADATTRIBUTE，或透過放置執行緒屬性，指定執行緒模型，然後以 [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) 指定非預設進入點。  
  
 如果在原始程式碼中指定的執行緒模型與以 \/CLRTHREADATTRIBUTE 指定的執行緒模型不一致時，連結器將忽略 \/CLRTHREADATTRIBUTE，並套用原始程式碼中指定的執行緒模型。  
  
 例如，如果您的 CLR 程式裝載了使用單一執行緒的 COM 物件，您將必須使用單一執行緒。如果您的 CLR 程式使用多執行緒，它就不能裝載使用單一執行緒的 COM 物件。  
  
### 若要在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 \[**屬性頁**\] 對話方塊。  如需詳細資訊，請參閱 [如何：開啟專案屬性頁](../../misc/how-to-open-project-property-pages.md)。  
  
2.  展開 \[**組態屬性**\] 節點。  
  
3.  展開 **\[連結器\]** 節點。  
  
4.  請選取 \[**進階**\] 屬性頁。  
  
5.  修改 \[**CLR 執行緒屬性**\] 屬性 \(Property\)。  
  
### 若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRThreadAttribute%2A>。  
  
## 請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)