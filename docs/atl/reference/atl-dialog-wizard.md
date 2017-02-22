---
title: "ATL 對話方塊精靈 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.codewiz.class.atl.dlg.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 對話方塊精靈"
  - "ATL 專案, 加入對話方塊資源"
ms.assetid: b0b9ace5-83c9-40d3-82c3-eb6293f10583
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 10
---
# ATL 對話方塊精靈
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

這個精靈會將衍生自 [CAxDialogImpl](../../atl/reference/caxdialogimpl-class.md) 的 ATL 對話方塊物件插入至專案。  衍生自 `CAxDialogImpl` 的對話方塊可裝載 ActiveX 控制項。  
  
 精靈會建立具有預設 \[**確定**\] 和 \[取消\] 按鈕的對話方塊資源。  您可使用 \[資源檢視\] 中的[對話方塊編輯器](../../mfc/dialog-editor.md)編輯對話方塊資源和加入 ActiveX 控制項。  
  
 精靈會將[訊息對應](../../atl/message-maps-atl.md) \(Message Map\) 和宣告插入至標頭檔 \(Header File\) 來處理預設 Click 事件。  如需關於 ATL 對話方塊的詳細資訊，請參閱[實作對話方塊](../../atl/implementing-a-dialog-box.md)。  
  
 **簡短名稱**  
 設定 ATL 對話方塊物件的縮寫名稱。  您所提供的名稱將決定類別名稱和檔案 \(.cpp 和 .h\) 名稱，除非您個別變更這些欄位。  
  
 `Class`  
 設定要建立類別的名稱。  這個名稱會根據您在 \[簡短名稱\] 中提供的名稱來命名，並在前端加上類別名稱慣用的前置字元 'C'。  
  
 **.h 檔案**  
 為新物件類別設定標頭檔 \(Header File\) 的名稱。  依照預設，這個名稱會根據您在 \[簡短名稱\] 中提供的名稱來命名。  按一下省略按鈕，將檔名儲存至您選擇的位置，或將類別宣告附加至現有的檔案。  如果您選擇現有檔案，除非您在精靈中按一下 \[完成\]，否則精靈不會將檔案儲存到選取位置。  
  
 精靈不會覆寫檔案。  如果您選取現有檔案的名稱，則當您按一下 \[完成\] 時，精靈會提示您是否要將類別宣告附加至檔案內容。  按一下 \[**是**\] 會將類別宣告附加至檔案，按一下 \[**否**\] 則可回到精靈並指定另一個檔名。  
  
 **.cpp 檔**  
 為新物件類別設定實作檔 \(Implementation File\) 的名稱。  依照預設，這個名稱會根據您在 \[簡短名稱\] 中提供的名稱來命名。  按一下省略按鈕，將檔名儲存至您選擇的位置。  除非您在精靈中按一下 \[完成\]，否則精靈不會將檔案儲存到選取位置。  
  
 精靈不會覆寫檔案。  如果您選取現有檔案的名稱，則當您按一下 \[完成\] 時，精靈會提示您是否要將類別實作 附加至檔案內容。  按一下 \[**是**\] 會將類別宣告附加至檔案，按一下 \[**否**\] 則可回到精靈並指定另一個檔名。  
  
## 請參閱  
 [ATL Dialog Box](../../atl/reference/adding-an-atl-dialog-box.md)