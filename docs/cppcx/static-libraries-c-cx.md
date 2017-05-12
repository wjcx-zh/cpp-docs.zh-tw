---
title: "靜態程式庫 (C++/CX) | Microsoft Docs"
ms.custom: ""
ms.date: "02/03/2017"
ms.prod: "windows-client-threshold"
ms.technology: ""
ms.reviewer: ""
ms.suite: ""
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
caps.latest.revision: 10
author: "ghogen"
ms.author: "ghogen"
manager: "ghogen"
caps.handback.revision: 10
---
# 靜態程式庫 (C++/CX)
[!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式中所使用的靜態程式庫可包含 ISO 標準 C\+\+ 程式碼 \(包括 STL 型別\)，以及未從 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式平台排除的 Win32 API 呼叫。 靜態程式庫可使用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]元件，並且可在特定限制下建立 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]元件。  
  
## 建立靜態程式庫  
  
#### 若要建立用於 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式中的靜態程式庫  
  
1.  在功能表列上，依序選擇 \[**檔案**\] \> \[**新增**\] \> \[**專案**\] \> \[**空白靜態程式庫 \([!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式\)**\]。  
  
2.  在 \[**方案總管**\] 中，開啟專案的捷徑功能表，然後選擇 \[**屬性**\]。 在 \[**屬性**\] 對話方塊中的 \[**組態屬性**\] \> \[**一般**\] 頁面上，將 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式支援設為 \[**是**\]。  
  
3.  在 \[組態屬性\] \> \[C\/C\+\+\] 頁面上，將 \[使用 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 擴充功能\] 設為 \[是 \(\/ZW\)\]。  
  
 當您編譯新的靜態程式庫時，如果您呼叫了排除於 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)] 應用程式以外的 Win32 API，編譯器將會引發錯誤 C3861：「找不到識別項」。 若要尋找支援 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 的替代方法，請參閱 [Alternatives to Windows APIs in Windows Store apps](http://msdn.microsoft.com/zh-tw/75568012-61e0-41cc-a4df-c698f54f21ec)。  
  
 如果您將 C\+\+ 靜態程式庫專案新增至 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]應用程式方案，您可能必須更新程式庫專案的屬性設定，使 [!INCLUDE[win8_appname_long](../cppcx/includes/win8-appname-long-md.md)]支援屬性設為 \[**是**\]。 若未進行此設定，程式碼仍會建置並連結，但在您嘗試驗證 [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)]的應用程式時將會發生錯誤。 靜態程式庫必須以使用它的專案相同的編譯器設定進行編譯。  
  
 如果您使用會建立公用 `ref` 類別、公用介面類別或公用實值類別的靜態程式庫，連結器將會引發下列警告：  
  
> **warning LNK4264:** 正在將以 \/ZW 編譯的目的檔封存至靜態程式庫，請注意，在撰寫 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 類型時，不建議與包含 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)] 中繼資料的靜態程式庫連結。  
  
 只有在靜態程式庫不會產生在程式庫本身以外使用的 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]元件，您才可以放心忽略此警告。 如果程式庫不會使用它所定義的元件，則連結器最佳化會將實作去除，即使公用中繼資料包含型別資訊。 這表示靜態程式庫中的公用元件會進行編譯，但不會在執行階段啟動。 因此，預定不供其他元件或應用程式使用的任何 [!INCLUDE[wrt](../cppcx/includes/wrt-md.md)]元件，都必須在動態連結程式庫 \(DLL\) 中實作。  
  
## 請參閱  
 [執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md)