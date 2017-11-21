---
title: "Dll (C + + /CX) |Microsoft 文件"
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
caps.latest.revision: "21"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: a3202ba5bd5b42b3f4853348258d5c4e3e5a2072
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="dlls-ccx"></a>DLL (C++/CX)
您可以使用 Visual Studio 建立的標準 Win32 DLL 或 Windows 執行階段元件可供通用 Windows 平台應用程式的 DLL。 使用 Visual Studio 或早於 Visual Studio 2012 可能不會載入正確的通用 Windows 平台應用程式，並可能無法通過應用程式驗證測試，在 Visual c + + 編譯器的版本所建立的標準 DLL [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)]。  
  
## <a name="windows-runtime-component-dlls"></a>Windows 執行階段元件 Dll  
 在大多數情況下，當您想要建立通用 Windows 平台應用程式中使用的 DLL，則建立 Windows 執行階段元件使用該名稱的專案範本。 您可以建立 Windows 執行階段元件專案，適用於具有公用或私用的 Windows 執行階段類型的 Dll。 Windows 執行階段元件可以從任何 Windows 執行階段相容語言撰寫的應用程式存取。 根據預設，Windows 執行階段元件的編譯器設定專案使用**/ZW**切換。 .winmd 檔案必須具有根命名空間的相同名稱。 例如，名為 A.B.C.MyClass 的類別必須在名為 A.winmd、A.B.winmd 或 A.B.C.winmd 的中繼資料檔案中定義，才能執行個體化。 DLL 的名稱不需符合 .winmd 檔案名稱。  
  
 如需詳細資訊，請參閱 [Creating Windows Runtime Components in C++](/MicrosoftDocs/windows-uwp/blob/docs/windows-apps-src/winrt-components/creating-windows-runtime-components-in-cpp.md)。  
  
#### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>若要參考的協力廠商 Windows 執行階段元件專案中的二進位  
  
1.  針對將要使用 DLL 的專案開啟捷徑功能表，然後選擇 [ **屬性**]。 在 [ **一般屬性** ] 頁面上，選擇 [ **加入新參考** ] 按鈕。  
  
2.  Windows 執行階段元件是由 DLL 檔和包含的中繼資料的.winmd 檔案所組成。 這些檔案通常位於相同的資料夾中。 在 [ **加入參考** ] 對話方塊的左窗格中選擇 [ **瀏覽** ] 按鈕，然後巡覽至 DLL 及其 .winmd 檔案的所在位置。 如需詳細資訊，請參閱 [教學課程：建立和使用擴充功能 SDK](http://msdn.microsoft.com/en-us/001e2fca-3d56-43ab-a5e0-0561d085679f)。  
  
## <a name="standard-dlls"></a>標準 DLL  
 您可以建立的標準 DLL 的 c + + 程式碼不會取用或產生公用 Windows 執行階段類型，使用從通用 Windows 平台應用程式。 當您只是要移轉現有的 DLL，以便在這個版本的 Visual Studio 中進行編譯，但無法轉換成 Windows 執行階段元件專案的 程式碼時，請使用通用 Windows 平台 DLL 專案類型。 當您進行下列步驟時，這個 DLL 將會隨 .appx 封裝中的應用程式可執行檔一起部署。  
  
#### <a name="to-create-a-standard-dll-in-visual-studio"></a>在 Visual Studio 中建立標準 DLL  
  
1.  在功能表列上選擇 **檔案**，**新增**，**專案**，然後選取 通用 Windows 平台 DLL 範本。  
  
2.  輸入專案的名稱，然後選擇 [ **確定** ] 按鈕。  
  
3.  新增程式碼。 請確定為您要匯出的函式使用 `__declspec(dllexport)` ，例如 `__declspec(dllexport) Add(int I, in j);`。  
  
4.  新增`#include winapifamily.h`納入該標頭檔從 Windows SDK，針對通用 Windows 平台應用程式，並設定巨集`WINAPI_FAMILY=WINAPI_PARTITION_APP`。  
  
#### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>若要從相同的方案參考標準 DLL 專案  
  
1.  針對將要使用 DLL 的專案開啟捷徑功能表，然後選擇 [ **屬性**]。 在 [ **一般屬性** ] 頁面上，選擇 [ **加入新參考** ] 按鈕。  
  
2.  在左窗格中選取 [ **方案**]，然後在右窗格中選取適當的核取方塊。  
  
3.  在您的原始程式碼檔中，視需要為 DLL 標頭檔新增 `#include` 陳述式。  
  
#### <a name="to-reference-a-standard-dll-binary"></a>若要參考標準 DLL 二進位檔  
  
1.  將 DLL 檔、.lib 檔和標頭檔複製並貼至已知位置，例如您目前的專案資料夾。  
  
2.  針對將要使用 DLL 的專案開啟捷徑功能表，然後選擇 [ **屬性**]。 在 [ **組態屬性**]、[ **連結器**]、[ **輸入** ] 頁面上，將 .lib 檔新增為相依性。  
  
3.  在您的原始程式碼檔中，視需要為 DLL 標頭檔新增 `#include` 陳述式。  
  
#### <a name="to-migrate-an-existing-win32-dll-for-universal-windows-platform-app-compatibility"></a>若要移轉現有的 Win32 DLL，針對通用 Windows 平台應用程式相容性  
  
1.  建立通用 Windows 平台 DLL 類型的專案，並加入您現有的原始程式碼。  
  
2.  新增`#include winapifamily.h`納入該標頭檔從 Windows SDK，針對通用 Windows 平台應用程式，並設定巨集`WINAPI_FAMILY=WINAPI_PARTITION_APP`。  
  
3.  在您的原始程式碼檔中，視需要為 DLL 標頭檔新增 `#include` 陳述式。  
  

