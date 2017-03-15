---
title: "ATL 精靈加入 ATL 支援的詳細資訊 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.atl.support
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: aa66bad0-008f-4886-94c1-2a0a0d04bce4
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: e353df6f4f6e728fb7b866fc7690215be28b8155
ms.lasthandoff: 02/24/2017

---
# <a name="details-of-atl-support-added-by-the-atl-wizard"></a>ATL 精靈加入 ATL 支援的詳細資訊
當您[將 ATL 支援加入至現有的 MFC 可執行檔或 DLL](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)，Visual c + + 可讓下列修改現有的 MFC 專案 (在此範例中，稱為專案`MFCEXE`):  
  
-   會加入兩個新檔案 （一個.idl 檔案和一個.rgs 檔案，用來註冊的伺服器）。  
  
-   在主應用程式標頭和實作檔案 （Mfcexe.h 和 Mfcexe.cpp） 中的新類別 (衍生自**CAtlMFCModule**) 加入。 程式碼加入至新的類別，除了`InitInstance`進行註冊。 程式碼也會加入至`ExitInstance`撤銷類別物件的函式。 在標頭檔，最後，兩個新標頭檔 （g 和 Mfcexe_i.c） 都包含在實作檔案中，宣告和初始化的新 Guid **CAtlMFCModule**-衍生的類別。  
  
-   若要正確登錄的伺服器，新.rgs 檔案的項目會加入專案的資源檔。  
  
## <a name="notes-for-dll-projects"></a>DLL 專案的相關資訊  
 當您將 ATL 支援加入 MFC DLL 專案時，您會看到一些差異。 程式碼加入至**DLLRegisterServer**和**DLLUnregisterServer**註冊及取消註冊 DLL 函式。 程式碼也會加入至[DllCanUnloadNow](../../atl/reference/catldllmodulet-class.md#dllcanunloadnow)和[DllGetClassObject](../../atl/reference/catldllmodulet-class.md#dllgetclassobject)。  
  
## <a name="see-also"></a>另請參閱  
 [MFC 專案中的 ATL 支援](../../mfc/reference/adding-atl-support-to-your-mfc-project.md)   
 [使用程式碼精靈加入功能](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [加入類別](../../ide/adding-a-class-visual-cpp.md)   
 [加入成員函式](../../ide/adding-a-member-function-visual-cpp.md)   
 [加入成員變數](../../ide/adding-a-member-variable-visual-cpp.md)   
 [覆寫虛擬函式](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [MFC 訊息處理常式](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [巡覽類別結構](../../ide/navigating-the-class-structure-visual-cpp.md)

