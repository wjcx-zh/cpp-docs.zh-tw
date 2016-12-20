---
title: "&lt;name&gt; is not a valid file name. | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VS_E_INVALIDFILENAME"
  - "VS.Message.0x00006A72"
ms.assetid: c5969671-3b64-4854-acb6-328e8a30863f
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# &lt;name&gt; is not a valid file name.
當嘗試從 \[命令\] 視窗建立新檔案，但在檔案名稱中包括不支援的字元時，就會發生這個錯誤。  
  
 檔案名稱不能包含下列字元：  
  
-   井字號 \(\#\)  
  
-   百分比 \(%\)  
  
-   連字號 \(&\)  
  
-   星號 \(\*\)  
  
-   垂直線 \(&#124;\)  
  
-   反斜線 \(\\\)  
  
-   冒號 \(:\)  
  
-   雙引號 \("\)  
  
-   小於 \(\<\)  
  
-   大於 \(\>\)  
  
-   句號 \(.\)  
  
-   問號 \(?\)  
  
-   正斜線 \(\/\)  
  
-   前置空格或尾端空格 \(' '\)  
  
-   Windows 或 DOS 的保留名稱  \(nul、aux、con、com1、lpt1 等等\)  
  
### 若要更正這個錯誤  
  
-   請輸入不包含上列字元的新檔名。  
  
## 請參閱  
 [新增檔案命令](../Topic/New%20File%20Command.md)   
 [Visual Studio 命令](../Topic/Visual%20Studio%20Commands.md)