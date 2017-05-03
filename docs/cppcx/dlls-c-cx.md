---
title: "DLL (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
caps.latest.revision: 21
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 21
---
# DLL (C++/CX)
您可以使用 Visual Studio 建立可供 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 應用程式使用的標準 Win32 DLL 或 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] 元件 DLL。 使用 [!INCLUDE[vs_dev11_long](../cppcx/includes/vs-dev11-long-md.md)] 以前的 Visual Studio 或 Visual C\+\+ 編譯器建立的標準 DLL 可能無法在 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式中正確載入，且可能無法通過 [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)]中的應用程式驗證測試。  
  
## [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 元件 DLL  
 在大部分的情況下，當您想建立用於 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] 應用程式的 DLL 時，請使用該名稱的專案範本，將其建立為 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 元件。 您可以為具有公用或私用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 型别的 DLL 建立 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 元件專案。[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]元件可從任何以 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]相容語言撰寫的應用程式存取。 根據預設，[!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 元件專案的編譯器設定會使用 **\/ZW** 參數。 .winmd 檔案必須具有根命名空間的相同名稱。 例如，名為 A.B.C.MyClass 的類別必須在名為 A.winmd、A.B.winmd 或 A.B.C.winmd 的中繼資料檔案中定義，才能執行個體化。 DLL 的名稱不需符合 .winmd 檔案名稱。  
  
 如需詳細資訊，請參閱[在 C\+\+ 中建立 Windows 執行階段元件](http://msdn.microsoft.com/library/5b7251e6-4271-4f13-af80-c1cf5b1489bf)。  
  
#### 在您的專案中參考協力廠商 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 元件二進位檔  
  
1.  針對將要使用 DLL 的專案開啟捷徑功能表，然後選擇 \[**屬性**\]。 在 \[**一般屬性**\] 頁面上，選擇 \[**加入新參考**\] 按鈕。  
  
2.  [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 元件由 DLL 檔和包含中繼資料的 .winmd 檔案組成。 這些檔案通常位於相同的資料夾中。 在 \[**加入參考**\] 對話方塊的左窗格中選擇 \[**瀏覽**\] 按鈕，然後巡覽至 DLL 及其 .winmd 檔案的所在位置。 如需詳細資訊，請參閱[教學課程：建立和使用擴充功能 SDK](http://msdn.microsoft.com/zh-tw/001e2fca-3d56-43ab-a5e0-0561d085679f)。  
  
## 標準 DLL  
 您可以建立適用於 C\+\+ 程式碼、且不會使用或產生公用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]類型的標準 DLL，並且從 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式使用它。 如果您只是想要移轉現有的 DLL，以便在這個 Visual Studio 版本中進行編譯，而不要將程式碼轉換為 Windows 執行階段元件專案，請使用 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] DLL 專案類型。 當您進行下列步驟時，這個 DLL 將會隨 .appx 封裝中的應用程式可執行檔一起部署。  
  
#### 在 Visual Studio 中建立標準 DLL  
  
1.  在功能表列上，依序選擇 \[**檔案**\]、\[**新增**\] 及 \[**專案**\]，然後選取 \[[!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] DLL\] 範本。  
  
2.  輸入專案的名稱，然後選擇 \[**確定**\] 按鈕。  
  
3.  新增程式碼。 請確定為您要匯出的函式使用 `__declspec(dllexport)`，例如 `__declspec(dllexport) Add(int I, in j);`。  
  
4.  新增 `#include winapifamily.h` 以從 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式的 Windows SDK 納入該標頭檔，並設定巨集 `WINAPI_FAMILY=WINAPI_PARTITION_APP`。  
  
#### 若要從相同的方案參考標準 DLL 專案  
  
1.  針對將要使用 DLL 的專案開啟捷徑功能表，然後選擇 \[**屬性**\]。 在 \[**一般屬性**\] 頁面上，選擇 \[**加入新參考**\] 按鈕。  
  
2.  在左窗格中選取 \[**方案**\]，然後在右窗格中選取適當的核取方塊。  
  
3.  在您的原始程式碼檔中，視需要為 DLL 標頭檔新增 `#include` 陳述式。  
  
#### 若要參考標準 DLL 二進位檔  
  
1.  將 DLL 檔、.lib 檔和標頭檔複製並貼至已知位置，例如您目前的專案資料夾。  
  
2.  針對將要使用 DLL 的專案開啟捷徑功能表，然後選擇 \[**屬性**\]。 在 \[**組態屬性**\]、\[**連結器**\]、\[**輸入**\] 頁面上，將 .lib 檔新增為相依性。  
  
3.  在您的原始程式碼檔中，視需要為 DLL 標頭檔新增 `#include` 陳述式。  
  
#### 若要移轉現有的 Win32 DLL，以相容於 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式  
  
1.  建立 \[[!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] DLL\] 類型的專案，並為其新增您現有的原始程式碼。  
  
2.  新增 `#include winapifamily.h` 以從 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式的 Windows SDK 納入該標頭檔，並設定巨集 `WINAPI_FAMILY=WINAPI_PARTITION_APP`。  
  
3.  在您的原始程式碼檔中，視需要為 DLL 標頭檔新增 `#include` 陳述式。  
  
## 請參閱  
 [\(NOTINBUILD\) 進階主題](http://msdn.microsoft.com/zh-tw/1ccff0cf-a6cc-47ef-a05f-eba6307b3ced)