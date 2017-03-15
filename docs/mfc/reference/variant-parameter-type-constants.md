---
title: "變異參數類型常數 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "VTS_YPOS_HIMETRIC"
  - "VTS_PICTURE"
  - "VTS_FONT"
  - "VTS_XPOS_HIMETRIC"
  - "VTS_XPOS_PIXELS"
  - "VTS_XSIZE_HIMETRIC"
  - "VTS_YPOS_PIXELS"
  - "VTS_TRISTATE"
  - "VTS_HANDLE"
  - "VTS_YSIZE_HIMETRIC"
  - "VTS_COLOR"
  - "VTS_OPTEXCLUSIVE"
  - "VTS_YSIZE_PIXELS"
  - "VTS_XSIZE_PIXELS"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "變異資料常數"
  - "變異"
  - "變異, 參數類型常數"
  - "VTS_COLOR 常數"
  - "VTS_FONT 常數"
  - "VTS_HANDLE 常數"
  - "VTS_OPTEXCLUSIVE 常數"
  - "VTS_PICTURE 常數"
  - "VTS_TRISTATE 常數"
  - "VTS_XPOS_HIMETRIC 常數"
  - "VTS_XPOS_PIXELS 常數"
  - "VTS_XSIZE_HIMETRIC 常數"
  - "VTS_XSIZE_PIXELS 常數"
  - "VTS_YPOS_HIMETRIC 常數"
  - "VTS_YPOS_PIXELS 常數"
  - "VTS_YSIZE_HIMETRIC 常數"
  - "VTS_YSIZE_PIXELS 常數"
ms.assetid: de99c7a9-7aae-4dc4-b723-40c6380543ab
caps.latest.revision: 14
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 15
---
# 變異參數類型常數
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

本主題列出表示為使用設計的不同的參數型別與 MFC 程式庫的 OLE automation 控制項類別的新的常數。  
  
 下列是類別常數的清單:  
  
##  <a name="_mfc_variant_data_constants"></a> 不同的資料常數  
  
-   **VTS\_COLOR** 的 32 位元整數用來表示 RGB 色彩值。  
  
-   對 OLE 字型物件的 **IFontDisp** 介面的**VTS\_FONT** 的指標。  
  
-   **VTS\_HANDLE** 視窗控制代碼值。  
  
-   對 OLE 圖片物件之 `IPictureDisp` 介面的**VTS\_PICTURE** 的指標。  
  
-   用於要用於控制項群組的控制項**VTS\_OPTEXCLUSIVE** 為 16 位元值，例如選項按鈕。  這個型別會告知容器，如果一個控制項群組中有 **TRUE** 值，就必須是 **FALSE**。  
  
-   用於可以有三個可能的其中一個值的屬性**VTS\_TRISTATE** 的 16 位元帶正負號的整數 \(選取，清除，無法使用\)，例如，核取方塊。  
  
-   在 **HIMETRIC** 單位用來表示沿著 X 軸的位置**VTS\_XPOS\_HIMETRIC** 的 32 位元不帶正負號的整數。  
  
-   在 **HIMETRIC** 單位用來代表沿著 Y 軸的位置**VTS\_YPOS\_HIMETRIC** 的 32 位元不帶正負號的整數。  
  
-   在像素用來表示沿著 X 軸的位置**VTS\_XPOS\_PIXELS** 的 32 位元不帶正負號的整數。  
  
-   在像素用來代表沿著 Y 軸的位置**VTS\_YPOS\_PIXELS** 的 32 位元不帶正負號的整數。  
  
-   **VTS\_XSIZE\_PIXELS** 的 32 位元不帶正負號的整數來表示螢幕物件的寬度 \(以像素為單位\)。  
  
-   **VTS\_YSIZE\_PIXELS** 的 32 位元不帶正負號的整數來表示螢幕物件的高度 \(以像素為單位\)。  
  
-   **VTS\_XSIZE\_HIMETRIC** 的 32 位元不帶正負號的整數來表示螢幕物件的寬度 \(以 **HIMETRIC** 單位。  
  
-   **VTS\_YSIZE\_HIMETRIC** 的 32 位元不帶正負號的整數來表示螢幕物件的高度 \(以 **HIMETRIC** 單位。  
  
    > [!NOTE]
    >  除了 **VTS\_FONT** 和 **VTS\_PICTURE**之外，其他不同的常數為所有不同的型別定義，，提供指標的不同資料常數。  使用 **VTS\_P**`constantname` 慣例，這些常數的名稱。  例如， **VTS\_PCOLOR** 是指向 **VTS\_COLOR** 常數。  
  
## 需求  
 **Header:** afxdisp.h  
  
## 請參閱  
 [巨集和全域](../../mfc/reference/mfc-macros-and-globals.md)