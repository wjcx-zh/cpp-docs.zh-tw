---
title: "ATL 專案中的 MFC 支援 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "vc.atl.addmfc"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ATL 專案, MFC 支援"
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# ATL 專案中的 MFC 支援
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

如果在 ATL 專案精靈中選取 \[支援 MFC\]，您的專案會將應用程式宣告為 MFC 應用程式物件 \(類別\)。  專案會初始化 MFC 程式庫並個體化衍生自 [CWinApp](../../mfc/reference/cwinapp-class.md) 的類別 \(*ProjName* 類別\)。  
  
 這個選項僅供非屬性化 ATL DLL 專案使用。  
  
```  
class CProjNameApp : public CWinApp  
{  
public:  
  
// Overrides  
   virtual BOOL InitInstance();  
   virtual int ExitInstance();  
   DECLARE_MESSAGE_MAP()  
};  
  
BEGIN_MESSAGE_MAP(CProjNameApp, CWinApp)  
END_MESSAGE_MAP()  
  
CProjNameApp theApp;  
  
BOOL CProjNameApp::InitInstance()  
{  
   return CWinApp::InitInstance();  
}  
  
int CProjNameApp::ExitInstance()  
{  
   return CWinApp::ExitInstance();  
}  
```  
  
 您可在 \[類別檢視\] 中檢視應用程式物件類別及其 `InitInstance` 和 `ExitInstance` 函式。  
  
## 請參閱  
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)   
 [預設的 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)