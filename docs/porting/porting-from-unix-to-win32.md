---
title: "從 UNIX 移植到 Win32 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- APIs [C++], porting to Win32
- Windows API [C++], migrating from UNIX
- migration [C++]
- UNIX [C++], porting to Win32
- porting to Win32 [C++], from UNIX
- porting to Win32 [C++]
- Win32 applications [C++], migrating from UNIX
ms.assetid: 3837e4fe-3f96-4f24-b2a1-7be94718a881
caps.latest.revision: 15
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 220ecd24c6056737d0338cc584663e4664ac81b1
ms.openlocfilehash: e6eefc285e5c82944426c185dd170cf498d4055c
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="porting-from-unix-to-win32"></a>從 UNIX 移植到 Win32
將應用程式從 UNIX 移轉至 Windows 時，有幾個選擇：  
  
-   使用 UNIX 程式庫，將應用程式從 UNIX 移植到 Win32  
  
-   將應用程式從 UNIX 原生地移植到 Win32  
  
-   使用 POSIX 子系統，在 Windows 上執行 UNIX 應用程式  
  
## <a name="unix-libraries"></a>UNIX 程式庫  
 UNIX 程式設計人員通常會考慮的一個做法是使用協力廠商 UNIX 類型程式庫，將 UNIX 程式碼編譯成 Win32 可執行檔。 許多商用 (且至少一個公用網域) 程式庫可以執行這項作業。 這個選擇適合一些應用程式。 這些移植程式庫的優點是可將初始移植投入時間降到最低。 對於競爭軟體產品而言，主要缺點則是應用程式的原生 Win32 移植通常會比較快，而且無疑地具有較多功能。 如果應用程式必須離開 UNIX Shell 呼叫 Win32，以取得更多 Windows 功能，可能會對應用程式造成不便。  
  
 下列清單提供有關將 UNIX 移轉至 Visual C++ 之移植和支援的 Microsoft 和協力廠商資源：  
  
### <a name="unix-migration-guides"></a>UNIX 移轉指南  
 《UNIX 自訂應用程式移轉指南》提供有關將程式碼從 UNIX 移轉至 Win32 環境的技術說明。  
  
 [http://go.microsoft.com/fwlink/?LinkId=95428](http://go.microsoft.com/fwlink/?LinkId=95428)  
  
 《Unix 移轉專案指南》藉由提供有關將大量專案從 UNIX 移轉至 Win32 的高階說明，來補充說明《UNIX 自訂應用程式移轉指南》。 該指南針對專案移轉的每個階段所要考量的問題，提出了建議。 您可以從下列網址進行下載：  
  
 [http://go.microsoft.com/fwlink/?linkid=20012](http://go.microsoft.com/fwlink/?linkid=20012)  
  
### <a name="microsoft-windows-services-for-unix-sfu"></a>Microsoft Windows Services for UNIX (SFU)  
 Microsoft Windows Services for UNIX (SFU) 針對將 Windows 整合至現有的 UNIX 環境，提供了全方位的跨平台服務。 Services for UNIX 提供檔案共用、遠端存取和管理、密碼同步處理、通用目錄管理、通用公用程式集和 Shell。  
  
 [Windows Services for UNIX](http://www.microsoft.com/downloads/details.aspx?FamilyID=896c9688-601b-44f1-81a4-02878ff11778&displaylang=en)  
  
### <a name="interopsystemscom"></a>InteropSystems.com  
 [http://www.interopsystems.com/](http://www.interopsystems.com/)  
  
 這個協力廠商的公司網站提供從 UNIX 移植到 Win32 的支援軟體。  
  
### <a name="c-boost-web-site"></a>C++ Boost 網站  
 [http://boost.sourceforge.net/regression-logs/](http://boost.sourceforge.net/regression-logs/)  
  
 [http://boost.sourceforge.net/boost-build2/](http://boost.sourceforge.net/boost-build2/)  
  
## <a name="porting-unix-applications-directly-to-win32"></a>直接將 UNIX 應用程式移植到 Win32  
 另一個做法是直接將 UNIX 應用程式移植到 Win32。 透過 ANSI C/C++ 程式庫和商用 C 編譯器程式庫，UNIX 應用程式所依賴的許多傳統系統呼叫都可以用於 Win32 應用程式中。  
  
 因為 Win32 主控台 API 會模擬 **stdio** 模型，並且存在使用 Win32 主控台 API 的 *curses* 版本，所以您不需要變更 **stdio** 應用程式的輸出模型。 如需詳細資訊，請參閱 [SetConsoleCursorPosition](http://msdn.microsoft.com/library/windows/desktop/ms686025)。  
  
 Berkeley Socket 應用程式只需少許變更就可以當成 Win32 應用程式來使用。 Windows Sockets 介面是為了 BSD 通訊端的可攜性而設計的，只需 WinSock 規格的簡介章節裡已經指出的極少變更部分。  
  
 Windows 支援符合 DCE 標準的 RPC，因此 RPC 應用程式都很容易使用。 請參閱 [RPC Functions](http://msdn.microsoft.com/library/windows/desktop/aa378623) (RPC 函式)。  
  
 大規模差異的其中一項是處理序模型。 UNIX 具有**分岔**，Win32 則沒有。 根據**分岔**和程式碼基底的用法，Win32 包含兩個可用的 API：**CreateProcess** 和 `CreateThread`。 您可以在 Win32 中重新設計將本身分岔成多個複本的 UNIX 應用程式，以使用多個處理序，或含有多個執行緒的單一處理程序。 如果使用多個處理序，有多種 IPC 方法可以用於處理序間的通訊 (而且在**分岔**提供的功能是必要時，也許會更新新處理序的程式碼和資料，讓它像其父代)。 如需 IPC 的詳細資訊，請參閱 [Interprocess Communications](http://msdn.microsoft.com/library/windows/desktop/aa365574) (處理序間通訊)。  
  
 Windows 和 UNIX 圖形模型差異極大。 UNIX 使用 X Window 系統 GUI，而 Windows 使用 GDI。 雖然在概念上類似，但是 X API 和 GDI API 之間沒有簡單的對應。 不過，針對移轉 UNIX OpenGL 應用程式已提供 OpenGL 支援， 而且還有適用於 Windows 的 X 用戶端和 X 伺服器。 如需 GDI 的相關資訊，請參閱[裝置內容](http://msdn.microsoft.com/library/windows/desktop/dd183553)。  
  
 基本 UNIX 應用程式 (包括許多 CGI 應用程式) 應該很容易移植到在 Windows 上執行的 Visual C++。 **open**、`fopen`、**read**、**write** 等函式在 Visual C++ 執行階段程式庫中都可以使用。 此外，C UNIX API 和 Win32 API 之間也有一對一對應：**open** 對應 **CreateFile**、**read** 對應 **ReadFile**、**write** 對應 **WriteFile**、`ioctl` 對應 **DeviceIOControl**、**close** 對應 **CloseFile** 等。  
  
## <a name="windows-posix-subsystem"></a>Windows POSIX 子系統  
 UNIX 程式設計人員還會考慮的另一個做法是使用 Windows POSIX 子系統。 不過，它只支援 POSIX 1003.1，這是建立 Windows NT 時唯一標準化的 POSIX 版本。 在這之後，由於大多數應用程式已轉換成 Win32，因此對於擴充這個子系統的需求很少。 完整功能的應用程式對 1003.1 系統不感興趣，因為它未包含許多功能 (例如 1003.2 的功能、網路支援等)。 在 Windows POSIX 子系統下執行之完整功能的應用程式無法存取 Win32 應用程式可用的 Windows 功能，例如記憶體對應檔案、網路和圖形。 VI、LS 和 GREP 等應用程式都是 Windows POSIX 子系統的主要目標。  
  
## <a name="see-also"></a>另請參閱  
 [Visual C++ 移植和升級指南](visual-cpp-change-history-2003-2015.md)   
 [UNIX](../c-runtime-library/unix.md)   
 [推斷規則](../build/inference-rules.md)
