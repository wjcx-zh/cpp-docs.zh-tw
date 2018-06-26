---
title: InitInstance 成員函式 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- InitInstance
dev_langs:
- C++
helpviewer_keywords:
- InitInstance method [MFC]
- applications [MFC], initializing
- MFC, initializing
- initializing MFC applications
ms.assetid: 4ef09267-ff7f-4c39-91a0-57454a264f83
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a9379fef6a1d676d6a3bc757ee51d5d27acd5f6f
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/25/2018
ms.locfileid: "36930172"
---
# <a name="initinstance-member-function"></a>InitInstance 成員函式
Windows 作業系統可讓您執行相同應用程式的多個複本或「執行個體」。 `WinMain` 呼叫[InitInstance](../mfc/reference/cwinapp-class.md#initinstance)每次啟動應用程式的新執行個體。  
  
 MFC 應用程式精靈所建立的標準 `InitInstance` 實作會執行下列工作：  
  
-   作為其主要動作，建立會依序建立文件、檢視和框架視窗的文件範本。 如需此程序的說明，請參閱[文件樣板建立](../mfc/document-template-creation.md)。  
  
-   從 .ini 檔或 Windows 登錄載入標準檔案選項，包括最近使用的檔案名稱。  
  
-   註冊一個或多個文件範本。  
  
-   對於 MDI 應用程式，建立一個主框架視窗。  
  
-   處理命令列，在命令列上開啟指定的文件或開啟新的空文件。  
  
 您可以加入自己的初始化程式碼或修改精靈所撰寫的程式碼。  
  
> [!NOTE]
>  MFC 應用程式必須初始化為單一執行緒 apartment (STA)。 如果您呼叫[CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279)中您`InitInstance`覆寫中，指定 COINIT_APARTMENTTHREADED （而非 COINIT_MULTITHREADED）。 如需詳細資訊，請參閱 < PRB: MFC 應用程式停止回應時初始化為多執行緒 Apartment （828643） 在應用程式[ http://support.microsoft.com/default.aspxscid=kb; en-us-我們; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643)。  
  
## <a name="see-also"></a>另請參閱  
 [CWinApp：應用程式類別](../mfc/cwinapp-the-application-class.md)
