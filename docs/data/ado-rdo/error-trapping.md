---
title: "錯誤截取 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ActiveX 控制項 [C++], 錯誤截取"
  - "錯誤截取 [C++]"
ms.assetid: c509b089-a542-44be-8f22-dc5832967a48
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# 錯誤截取
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在資料繫結中，錯誤截取來自兩個來源：錯誤事件或錯誤物件。  
  
##  <a name="vcreferrortrappingviaerrorevents"></a> 透過錯誤事件來進行錯誤截取  
 ADO 資料控制項和 RDO RemoteData 資料控制項都有錯誤事件。  一般而言，您會設定一個錯誤事件處理常式。  事件處理常式應具有以下簽章：  
  
```  
void CMyDlg::OnErrorAdodc1(long ErrorNumber,  
                           BSTR* FAR Description,  
                           long Scode,  
                           LPCTSTR Source,  
                           LPCTSTR HelpFile,  
                           long HelpContext,  
                           BOOL FAR* fCancelDisplay)  
```  
  
 通常描述欄位將會填入 \(Populate\) 資料，但 ErrorNumber 和 Scode 欄位則只在 COM 錯誤發生時，才填入資料。  標準的事件處理常式會在訊息方塊內顯示描述欄位。  例如：  
  
```  
{  
   USES_CONVERSION;     
// note: have to include the ATL file ATLConv.h to use the ATL conversion macros  
   ::AfxMessageBox(OLE2T(*Description), MB_OK);  
}  
```  
  
 不過，因為 ADO 資料控制項和 RDO RemoteData 控制項都已設成截取錯誤事件，所以不需要撰寫程式碼。  
  
##  <a name="vcreferrortrappingviaerrorobjects"></a> 透過錯誤物件來進行錯誤設陷  
 ADO 和 RDO 都有錯誤物件。  在產生[包裝函式類別](../../data/ado-rdo/wrapper-classes.md)時，RDO RemoteData 控制項會為錯誤物件產生包裝函式，而 ADO 資料控制項則不會。  
  
 ADO 資料控制項會自動顯示 ADO 錯誤訊息。  
  
## 請參閱  
 [在 Visual C\+\+ 中使用 ActiveX 控制項進行資料繫結](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md)