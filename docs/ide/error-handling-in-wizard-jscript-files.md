---
title: "精靈 JScript 檔案中的錯誤處理 | Microsoft Docs"
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
  - "錯誤處理, JScript"
  - "JScript, 處理錯誤"
  - "精靈 JScript 錯誤處理"
ms.assetid: 6df3ba46-7ab6-484c-ac45-b08f4b6a5900
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 精靈 JScript 檔案中的錯誤處理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您建立精靈時，您的專案會包含 Default.js 和 Common.js 檔案。  請使用這些檔案來自訂專案。  如需詳細資訊，請參閱 [JScript 檔案](../ide/jscript-file.md)。  
  
 您的專案應包含錯誤處理。  下列程式碼提供您這種程式碼的範例。  
  
### 若要處理 JScript 中的錯誤  
  
1.  若要在使用者按一下 \[完成\] 時擷取錯誤，請輸入下列程式碼：  
  
    ```  
    function OnFinish(selProj, Class)  
    {  
       try  
       {  
          .....  
       }  
       catch(e)  
       {  
          if (e.description.length != 0)  
             SetErrorInfo(e.description, e.number);  
          return e.number  
       }  
    }  
    ```  
  
2.  從此段指令碼所呼叫的任一 Helper Script 函式擲回 `e`：  
  
    ```  
    function ExtenderFromType(strVariableType)  
    {  
       try  
       {  
          ....  
       }  
       catch(e)  
       {  
          throw e;  
       }  
    }  
    ```  
  
3.  如果 **PREPROCESS\_FUNCTION** 參數位於 [.vsz 檔](../ide/dot-vsz-file-project-control.md)中，精靈便會呼叫 [CanAddATLClass](../ide/jscript-functions-for-cpp-wizards.md)。  如果失敗並傳回 **false**，請使用 [SetErrorInfo](../ide/seterrorinfo.md)：  
  
    ```  
    function CanAddATLClass(oProj, oObject)  
    {  
       try  
       {  
          if (!IsATLProject(oProj))  
          {  
             if (!IsMFCProject(oProj, true))  
             {     
                var L_CanAddATLClass_Text = "ATL classes can only be added  
     to ATL, MFC EXE and MFC regular DLL projects.";  
                wizard.ReportError(L_CanAddATLClass_Text);  
                return false;  
             }  
             else  
             {  
                .....  
                var bRet = AddATLSupportToProject(oProj);  
                .....  
                return bRet;  
             }  
          }  
          return true;  
       }  
       catch(e)  
       {  
          throw e;  
       }  
    }  
    ```  
  
4.  如果您必須返回**新增專案**或**加入新項目**對話方塊，請傳回 **VS\_E\_WIZBACKBUTTONPRESS**：  
  
    ```  
    function OnFinish(selProj, Class)  
    {  
       ....  
       if (!CheckAddtoProject(selProj))  
       {  
          return VS_E_WIZARDBACKBUTTONPRESS;  
       }  
    }  
    ```  
  
## 請參閱  
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [自訂精靈](../ide/customizing-your-wizard.md)