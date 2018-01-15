---
title: "DEVNAMES 結構 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: DEVNAMES
dev_langs: C++
helpviewer_keywords: DEVNAMES [MFC]
ms.assetid: aac97f60-2169-471a-ba5d-c0baed9eed9a
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a3627af10dfb6fd18c54f772d26c33123127613a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="devnames-structure"></a>DEVNAMES 結構
`DEVNAMES` 結構包含可識別印表機的驅動程式、裝置和輸出連接埠名稱的字串。  
  
## <a name="syntax"></a>語法  
  
```  
typedef struct tagDEVNAMES { /* dvnm */  
    WORD wDriverOffset;  
    WORD wDeviceOffset;  
    WORD wOutputOffset;  
    WORD wDefault; */* driver,
    device,
    and port-name strings follow wDefault */  
} DEVNAMES;  
```  
  
#### <a name="parameters"></a>參數  
 *wDriverOffset*  
 (輸入/輸出) 以字元為單位指定裝置驅動程式中包含檔名的以 Null 終止字串位移 (不含副檔名)。 在輸入時，這個字串用來決定對話方塊最初顯示的印表機。  
  
 *wDeviceOffset*  
 (輸入/輸出) 以字元為單位指定包含裝置名稱的以 Null 終止字串位移 (最多 32 個位元組，包括 Null)。 這個字串必須是相同**Devmode**隸屬[DEVMODE](http://msdn.microsoft.com/library/windows/desktop/dd183565)結構。  
  
 *wOutputOffset*  
 (輸入/輸出) 以字元為單位指定包含實體輸出媒介 (輸出連接埠) 之 DOS 裝置名稱的以 Null 終止字串位移。  
  
 *wDefault*  
 指定字串是否包含在 `DEVNAMES` 結構中，以識別預設印表機。 這個字串是用來驗證預設印表機自從上次進行列印作業以來是否並未變更。 輸入時，如果**DN_DEFAULTPRN**旗標設定，其他的值`DEVNAMES`結構會根據目前預設的印表機檢查。 如果沒有相符的字串，則顯示一個警告訊息，通知使用者文件可能需要重新格式化。 在輸出時， **wDefault**成員有所變更，只有當 [設定列印格式] 對話方塊出現，而且使用者選擇 [確定] 按鈕。 **DN_DEFAULTPRN**如果已選取預設的印表機設定旗標。 如果選取了特定的印表機，則不會設定旗標。 這個成員內的其他位元會保留給 [列印] 對話方塊程序在內部使用。  
  
## <a name="remarks"></a>備註  
 **PrintDlg**函式會使用這些字串來初始化系統定義的 [列印] 對話方塊中的成員。 當使用者關閉對話方塊時，所選取之印表機的資訊會在此結構中傳回。  
  
## <a name="requirements"></a>需求  
 **標頭：** commdlg.h  
  
## <a name="see-also"></a>請參閱  
 [結構、 樣式、 回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPrintDialog::CreatePrinterDC](../../mfc/reference/cprintdialog-class.md#createprinterdc)


