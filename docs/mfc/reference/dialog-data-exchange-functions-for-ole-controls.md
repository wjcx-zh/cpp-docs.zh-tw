---
title: "OLE 控制項的對話方塊資料交換函式 | Microsoft Docs"
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
  - "vc.mfc.macros.data"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "DDX (對話資料交換), OLE 支援"
  - "OLE 控制項, DDX 函式"
ms.assetid: 7ef1f288-ff65-40d4-aad2-5497bc00bb27
caps.latest.revision: 13
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 控制項的對話方塊資料交換函式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題列出 DDX\_OC 函式來 OLE automation 控制項的屬性之間交換資料在對話方塊中，表單或控制項檢視中檢視應用程式、對話方塊、表單檢視或控制項檢視應用程式的資料成員。  
  
### DDX\_OC 功能  
  
|||  
|-|-|  
|[DDX\_OCBool](../Topic/DDX_OCBool.md)|處理 **BOOL** 資料傳輸至 OLE automation 控制項之屬性和 **BOOL** 資料成員之間。|  
|[DDX\_OCBoolRO](../Topic/DDX_OCBoolRO.md)|處理 **BOOL** 資料傳輸至 OLE automation 控制項之唯讀屬性和 **BOOL** 資料成員之間。|  
|[DDX\_OCColor](../Topic/DDX_OCColor.md)|處理 **OLE\_COLOR** 資料傳輸至 OLE automation 控制項之屬性和 **OLE\_COLOR** 資料成員之間。|  
|[DDX\_OCColorRO](../Topic/DDX_OCColorRO.md)|處理 **OLE\_COLOR** 資料傳輸至 OLE automation 控制項之唯讀屬性和 **OLE\_COLOR** 資料成員之間。|  
|[DDX\_OCFloat](../Topic/DDX_OCFloat.md)|處理 **float** \( **double**\) 資料傳輸至 OLE automation 控制項之屬性和 **float** \( **double**\) 或資料成員之間。|  
|[DDX\_OCFloatRO](../Topic/DDX_OCFloatRO.md)|處理 **float** \( **double**\) 資料傳輸至 OLE automation 控制項之唯讀屬性和 **float** \( **double**\) 或資料成員之間。|  
|[DDX\_OCInt](../Topic/DDX_OCInt.md)|處理 `int` \( **long**\) 資料傳輸至 OLE automation 控制項之屬性和 `int` \( **long**\) 或資料成員之間。|  
|[DDX\_OCIntRO](../Topic/DDX_OCIntRO.md)|處理 `int` \( **long**\) 資料傳輸至 OLE automation 控制項之唯讀屬性和 `int` \( **long**\) 或資料成員之間。|  
|[DDX\_OCShort](../Topic/DDX_OCShort.md)|處理 **short** 資料傳輸至 OLE automation 控制項之屬性和 **short** 資料成員之間。|  
|[DDX\_OCShortRO](../Topic/DDX_OCShortRO.md)|處理 **short** 資料傳輸至 OLE automation 控制項之唯讀屬性和 **short** 資料成員之間。|  
|[DDX\_OCText](../Topic/DDX_OCText.md)|處理 **CString** 資料傳輸至 OLE automation 控制項之屬性和 **CString** 資料成員之間。|  
|[DDX\_OCTextRO](../Topic/DDX_OCTextRO.md)|處理 **CString** 資料傳輸至 OLE automation 控制項之唯讀屬性和 **CString** 資料成員之間。|  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)