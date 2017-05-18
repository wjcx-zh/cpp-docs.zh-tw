---
title: "MFC DLL 精靈、 應用程式設定 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.appwiz.mfc.dll.appset
dev_langs:
- C++
helpviewer_keywords:
- MFC DLL Wizard, application settings
ms.assetid: 0a96b94f-ae36-4975-951b-c9ffb3def21c
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: df1e3de3e1548fe4c4c340a30127d9916998ba64
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="application-settings-mfc-dll-wizard"></a>MFC DLL 精靈、應用程式設定
使用 MFC DLL 精靈的這個頁面來設計和加入新的 MFC DLL 專案的基本功能。  
  
## <a name="dll-type"></a>DLL 的類型  
 選取您想要建立之 DLL 的類型。  
  
 **使用共用的 MFC DLL 的標準 DLL**  
 選取此選項即可連結 MFC 程式庫當做共用 DLL 程式。 使用此選項，您無法共用 MFC 物件 DLL 和程式之間呼叫的應用程式。 您的程式在執行階段會呼叫 MFC 程式庫。 如果它包含多個使用 MFC 程式庫的執行檔，此選項會降低您的程式的磁碟和記憶體需求。 Win32 和 MFC 程式可以在 DLL 中呼叫函式。 您必須轉散發 MFC DLL，這種類型的專案。  
  
 **Mfc 靜態連結的標準 DLL**  
 選取此選項可在建置階段將程式以靜態方式連結至 MFC 程式庫。 Win32 和 MFC 程式可以在 DLL 中呼叫函式。 雖然此選項會增加程式的大小，您不需要轉散發 MFC DLL，這種類型的專案。 您無法在您的 DLL 和呼叫的應用程式之間共用 MFC 物件。  
  
 **MFC 擴充 DLL**  
 如果您想讓程式在執行階段，發出呼叫 MFC 程式庫，而且如果您想要共用您的 DLL 和呼叫的應用程式之間的 MFC 物件，請選取此選項。 如果它所包含的所有使用 MFC 程式庫的多個可執行檔，此選項會降低您的程式、 磁碟和記憶體需求。 只有 MFC 程式可以在 DLL 中呼叫函式。 您必須轉散發 MFC DLL，這種類型的專案。  
  
## <a name="additional-features"></a>其他功能  
 選取是否 MFC DLL 應支援 automation，以及是否應可支援 Windows 通訊端。  
  
 **自動化**  
 選取**自動化**讓程式操作另一個程式中實作的物件。 選取**自動化**也會公開給其他自動化用戶端程式。 請參閱[自動化](../../mfc/automation.md)如需詳細資訊。  
  
 **Windows 通訊端**  
 選取此選項以指出您的程式支援 Windows 通訊端。 Windows 通訊端，可讓您撰寫的程式可透過 TCP/IP 網路通訊。  
  
 建立支援您的 MFC DLL 與 Windows 通訊端時， [cwinapp:: Initinstance](../../mfc/reference/cwinapp-class.md#initinstance)初始化支援通訊端與 MFC 標頭檔 StdAfx.h 包含 AfxSock.h。  
  
## <a name="see-also"></a>另請參閱  
 [MFC DLL 精靈](../../mfc/reference/mfc-dll-wizard.md)   
 [建立 MFC DLL 專案](../../mfc/reference/creating-an-mfc-dll-project.md)


