---
title: 應用程式設定、 Win 32 專案精靈 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.appwiz.win32.appset
dev_langs:
- C++
helpviewer_keywords:
- application settings [C++]
- Win32 Project Wizard, application settings
ms.assetid: d6b818f0-9b23-4793-a6c5-df1c8c594bad
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d6d2cd31306baaa0d9c8f137122fed1d4ae97295
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/02/2018
ms.locfileid: "39464680"
---
# <a name="application-settings-win-32-project-wizard"></a>Win 32 應用程式精靈、應用程式設定
使用精靈的這個頁面來設定 Win32 專案的選項。  
  
 **應用程式類型**  
 建立指定的應用程式類型。  
  
|選項|描述|  
|------------|-----------------|  
|**主控台應用程式**|建立主控台應用程式 (Console Application)。 以開發主控台程式[主控台函式](https://msdn.microsoft.com/library/ms813137.aspx)，提供在主控台視窗中的字元模式支援。 Visual c + +[執行階段程式庫](../c-runtime-library/c-run-time-library-reference.md)也提供輸出，並從主控台視窗，使用標準 I/O 函式，這類輸入`printf_s()`和`scanf_s()`。 主控台應用程式有沒有圖形化使用者介面。 它會編譯為.exe 檔案，並可當做獨立的應用程式，從命令列來執行。<br /><br /> 您可以新增 MFC 與 ATL 支援新增至主控台應用程式。|  
|**Windows 應用程式**|建立 Win32 程式。 Win32 程式是在 C 或 c + +，來建立圖形化使用者介面中使用 Win32 API 的呼叫中所撰寫的可執行檔應用程式 (EXE)。<br /><br /> 您無法新增 MFC 或 ATL 支援加入至 Windows 應用程式。|  
|**DLL**|建立 Win32 動態連結程式庫 (DLL)。 Win32 DLL 是二進位檔案，C 或 c + +，使用呼叫 Win32 API，而不是 MFC 類別和做為多個應用程式可以同時使用的函式的共用程式庫撰寫的。<br /><br /> 您無法新增 MFC 或 ATL 支援加入至 DLL 的應用程式。 您可以指定由 DLL 匯出的符號。|  
|**靜態程式庫**|建立靜態程式庫。 靜態程式庫是包含物件和其功能與資料，用來建置可執行檔時，連結到您的程式檔案。 本主題說明如何建立初學者檔案和[專案屬性](../ide/property-pages-visual-cpp.md)靜態程式庫。 靜態程式庫檔案提供下列優點：<br /><br /> -如果您正在使用的應用程式呼叫 Win32 API，而不是 MFC 類別非常有用 Win32 靜態程式庫。<br />-無論您的 Windows 應用程式的其餘部分撰寫以 C 或 c + + 連結的程序都是一樣的。<br />-您可以在以 MFC 為基礎的程式或非 MFC 程式連結的靜態程式庫。|  
  
 **其他選項**  
 定義支援和應用程式，根據其類型的選項。  
  
|選項|描述|  
|------------|-----------------|  
|**空專案**|指定的專案檔案空白。 如果您有一組的原始程式檔 （例如.cpp 檔案、 標頭檔、 圖示、 工具列、 對話方塊和等等），而且想要在 Visual c + + 開發環境中建立專案，您必須先建立空白的專案，然後將檔案新增至專案。<br /><br /> 此選項不適用於靜態程式庫專案。|  
|**匯出符號**|指定 DLL 專案匯出的符號。|  
|**先行編譯標頭**|指定靜態程式庫專案會使用預先編譯的標頭。|  
|安全性開發生命週期 (SDL) 檢查|如需有關 SDL 的詳細資訊，請參閱[Microsoft 安全性開發生命週期 (SDL) 流程指引](../build/reference/sdl-enable-additional-security-checks.md)|  
  
 **新增的支援**  
 新增對其中一個提供 Visual c + + 程式庫支援。  
  
|選項|描述|  
|------------|-----------------|  
|**ATL**|會建置類別 Active Template Library (ATL) 的專案支援。 Win32 主控台應用程式只。<br /><br /> **請注意**這個選項不會指出加入 ATL 物件使用 ATL 程式碼精靈的支援。 您可以加入 ATL 物件到 ATL 專案或 ATL 與 MFC 專案支援。|  
|**MFC**|會建置 Microsoft Foundation Class (MFC) 程式庫的專案支援。 適用於 Win32 主控台應用程式和靜態程式庫。|  
  
## <a name="see-also"></a>另請參閱  
 [Win32 應用程式精靈](../windows/win32-application-wizard.md)   