---
title: ATL 精靈加入 ATL 支援的詳細資料 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.codewiz.atl.support
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 450021fd1ea05831f44dd5af7a9f1e39a9d6fc5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371780"
---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>ATL 精靈加入 ATL 支援的詳細資訊
當您[將 ATL 支援加入至現有的 MFC 可執行檔或 DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)，Visual c + + 可讓下列修改現有的 MFC 專案 (在此範例中，稱為專案`MFCEXE`):  
  
-   會加入兩個新的檔案 （.idl 檔案和用來註冊伺服器.rgs 檔案）。  
  
-   在主應用程式標頭與實作檔 （Mfcexe.h 和 Mfcexe.cpp） 的新類別 (衍生自**CAtlMFCModule**) 加入。 程式碼加入至新的類別，除了`InitInstance`進行註冊。 程式碼也會加入至`ExitInstance`撤銷類別物件的函式。 標頭檔，最後，兩個新標頭檔 （h 和 Mfcexe_i.c） 包含在實作檔案中，宣告和初始化的新 Guid **CAtlMFCModule**-衍生的類別。  
  
-   若要正確地註冊伺服器，新.rgs 檔案項目會加入至專案的資源檔。  
  
## <a name="notes-for-dll-projects"></a>DLL 專案的附註  
 當您將 ATL 支援加入 MFC DLL 專案時，您會看到的一些差異。 程式碼加入至**DLLRegisterServer**和**DLLUnregisterServer**註冊及取消註冊 DLL 函式。 程式碼也會加入至[DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow)和[DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 專案中的 ATL 支援](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)
