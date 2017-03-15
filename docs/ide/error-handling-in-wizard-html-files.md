---
title: "精靈 HTML 檔案中的錯誤處理 | Microsoft Docs"
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
  - "錯誤處理, 檔案錯誤檢查"
  - "HTML, 錯誤處理"
ms.assetid: eb428a64-b681-4420-987d-92098bf98455
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# 精靈 HTML 檔案中的錯誤處理
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

當您建立具有使用者介面的精靈時，您的專案會包含 .htm 檔案。  請使用這些檔案來自訂專案。  如需詳細資訊，請參閱 [HTML 檔](../ide/html-files.md)。  
  
 您的專案應包含錯誤處理。  下列程式碼提供您這種程式碼的範例。  
  
### 若要處理 HTML 中的錯誤  
  
1.  驗證欄位時，如果您在 DLL 中呼叫驗證方法 \(其應設定錯誤資料\)，請呼叫不帶參數的 `ReportError`。  
  
    ```  
    function ValidateInput()  
    {  
       if (!window.external.ValidateFile(HEADER_FILE.value))  
       {  
          ReportError();  
          HEADER_FILE.focus();  
          return false;  
       }  
    }  
    ```  
  
2.  當您驗證欄位時，如果只使用 HTML 指令碼驗證欄位，請先呼叫 `SetErrorInfo`，然後呼叫不帶參數的 `ReportError`。  
  
    ```  
    function OnWhatever()  
    {  
       if (!ValidateInput())  
          window.external.ReportErrror();  
       ....  
    }  
  
    function ValidateInput()  
    {  
       .....  
  
       if (HEADER_FILE.value == IMPL_FILE.value)  
       {  
          var L_ErrMsg_Text = "Header and implementation files cannot have the same name.";  
          SetErrorInfo(L_ErrMsg_Text);  
          bValid = false;  
       }  
       if (TYPE.value == "")  
       {  
          var L_ErrMsg4_Text = "Type cannot be blank.";  
          SetErrorInfo(L_ErrMsg4_Text);  
          bValid = false;  
       }  
       return bValid;  
    }  
    ```  
  
3.  呼叫帶參數的 `ReportError`：  
  
    ```  
    function ValidateInput()  
    {  
       if (!IsListed(strType))  
       {  
          var L_Invalid2_Text = "The variable type should be one of the types listed.";  
          window.external.ReportError(L_Invalid2_Text);  
          VariableType.focus();  
          return false;  
       }  
    }  
    ```  
  
4.  如果您必須返回**新增專案**或**加入新項目**對話方塊，請傳回 **VS\_E\_WIZBACKBUTTONPRESS**：  
  
    ```  
    try  
    {  
       oCM   = window.external.ProjectObject.CodeModel;  
    }  
    catch(e)  
    {  
       var L_NCBError_Text = "Cannot access the Class View information   
    file. Class View information will not be available.";  
       window.external.ReportError(L_NCBError_Text);  
       return VS_E_WIZARDBACKBUTTONPRESS;  
    ```  
  
## 請參閱  
 [您的精靈所建立的檔案](../ide/files-created-for-your-wizard.md)   
 [自訂精靈](../ide/customizing-your-wizard.md)