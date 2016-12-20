---
title: "OLE 控制項的持續性 | Microsoft Docs"
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
  - "vc.mfc.macros.ole"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "OLE 控制項, 保存性"
  - "保存性, OLE 控制項"
ms.assetid: 64f8dc80-f110-41af-b3ea-14948f6bfdf7
caps.latest.revision: 17
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OLE 控制項的持續性
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

OLE 控制項的其中一個功能是屬性持續性 \(或序列化\)，允許 OLE 控制項來回檔案讀取或寫入屬性值或資料流。  在應用程式已終結控制項之後，容器應用程式可以使用序列化儲存控制項的屬性值。  當一個控制項的新執行個體在稍後被建立，OLE 控制項的屬性值可以從檔案或資料流被讀取。  
  
### OLE 控制項的持續性  
  
|||  
|-|-|  
|[PX\_Blob](../Topic/PX_Blob.md)|交換儲存二進位大型物件 \(BLOB\) \(BLOB\) 資料的控制項屬性。|  
|[PX\_Bool](../Topic/PX_Bool.md)|交換型別 **BOOL** 的控制項屬性。|  
|[PX\_Color](../Topic/PX_Color.md)|交換控制項的色彩屬性。|  
|[PX\_Currency](../Topic/PX_Currency.md)|交換型別 **CY** 的控制項屬性。|  
|[PX\_DataPath](../Topic/PX_DataPath.md)|交換型別 `CDataPathProperty` 的控制項屬性。|  
|[PX\_Double](../Topic/PX_Double.md)|交換型別 **double** 的控制項屬性。|  
|[PX\_Font](../Topic/PX_Font.md)|交換控制項的字型屬性。|  
|[PX\_Float](../Topic/PX_Float.md)|交換型別 **float** 的控制項屬性。|  
|[PX\_IUnknown](../Topic/PX_IUnknown.md)|交換未定義型別的控制項屬性。|  
|[PX\_Long](../Topic/PX_Long.md)|交換型別 **long** 的控制項屬性。|  
|[PX\_Picture](../Topic/PX_Picture.md)|交換控制項的圖片屬性。|  
|[PX\_Short](../Topic/PX_Short.md)|交換型別 **short** 的控制項屬性。|  
|[PX\_ULong](../Topic/PX_ULong.md)|交換型別 **ULONG** 的控制項屬性。|  
|[PX\_UShort](../Topic/PX_UShort.md)|交換型別 **USHORT** 的控制項屬性。|  
|[PX\_String](../Topic/PX_String.md)|交換字元字串控制項屬性。|  
|[PX\_VBXFontConvert](../Topic/PX_VBXFontConvert.md)|交換 VBX 控制項的字型相關屬性至 OLE 控制項的字型屬性。|  
  
 此外，提供 `AfxOleTypeMatchGuid` 全域函式來測試 `TYPEDESC` 中與指定之 GUID 之間的符合。  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)