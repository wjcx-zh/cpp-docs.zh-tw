---
title: "ATL 專案中的 MFC 支援 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: vc.atl.addmfc
dev_langs: C++
helpviewer_keywords: ATL projects, MFC support
ms.assetid: f90b4276-cb98-4c11-902c-9ebcfe6f954b
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 0217c62ff207ad706dbcb1cd172e878c2b96daee
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="mfc-support-in-atl-projects"></a>ATL 專案中的 MFC 支援
如果您選取**支援 MFC** ATL 專案精靈，在您的專案也會宣告為 MFC 應用程式物件 （類別） 的應用程式。 初始化 MFC 程式庫專案，並具現化類別 (類別*ProjName*) 衍生自[CWinApp](../../mfc/reference/cwinapp-class.md)。  
  
 未使用屬性的 ATL DLL 專案只能使用此選項。  
  
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
  
 您可以檢視應用程式的物件類別和其`InitInstance`和`ExitInstance`類別檢視中的函式。  
  
## <a name="see-also"></a>另請參閱  
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [建立的 ATL 專案](../../atl/reference/creating-an-atl-project.md)   
 [預設 ATL 專案組態](../../atl/reference/default-atl-project-configurations.md)

