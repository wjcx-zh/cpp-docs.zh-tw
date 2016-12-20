---
title: "Resource transformation for file &#39;file&#39; failed. &lt;reason&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vs.tasklisterror.resx_generator_failed"
ms.assetid: 6b537d38-1da9-4f5f-9ae9-1f26e260c2ac
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# Resource transformation for file &#39;file&#39; failed. &lt;reason&gt;
授權處理器失敗，而無法將 .resx 檔案轉換成二進位 .resources 檔案。  特定原因 \(如果有的話\) 會附加到字串結尾。  如果發生這種錯誤，建置處理序將無法完成。  
  
 最可能導致這個錯誤的原因是錯誤的 .resx 檔案。  例如，檔案可能曾在文字編輯器中開啟和修改過。  
  
 如果您收到的原因是「已加入項目。  字典中的索引鍵：'NewControlName.\<Property Name\>' 加入的索引鍵：'ControlName.\<Property Name\>'」，請閱讀以下的步驟並依此來重現及修正這個錯誤。  
  
### 若要重現這個錯誤  
  
1.  建立新的 Windows 應用程式。  預設會建立 Form1。  
  
2.  在 \[**檢視**\] 功能表上，按一下 \[**屬性**\]。  
  
3.  在 \[**屬性**\] 視窗中，將 \[**Localizable**\] 屬性設定為 `True`。  
  
4.  在 \[**屬性**\] 視窗中，按一下 \[**語言**\]，並將值設定為 \[日文\]。  
  
5.  從工具箱將按鈕拖曳到表單上。  
  
6.  將按鈕名稱 "Button1" 變更為 "BUTTON1"。  
  
7.  在 \[**建置**\] 功能表上，按一下 \[**建置方案**\]。  
  
### 若要更正這個錯誤  
  
1.  在 \[**檔案**\] 功能表上，將游標指向 \[**開啟**\]，然後按一下 \[**檔案**\]。  
  
2.  找出 Form1.resx 檔案，然後按一下 \[**確定**\]。  Form1.resx 隨即顯示。  
  
3.  找出原始關鍵值，然後以手動方式將它們從資料清單中刪除。  例如，您有一個按鈕名為 "Button1"。  接著，您將這個按鈕的名稱修改為 "BUTTON1"。  於是，Form1.resx 中同時存在 "Button1" 和 "BUTTON1" 關鍵值。  請移除所有 "Button1" 項目，然後重建專案。  
  
## 請參閱  
 [Resources in .Resx File Format](http://msdn.microsoft.com/zh-tw/0c476133-87e4-47e8-b0ef-4b88f4ef3dc5)   
 [File Types and File Extensions in Visual Basic and Visual C\#](http://msdn.microsoft.com/zh-tw/f793852c-da06-4d52-a826-65f635844772)