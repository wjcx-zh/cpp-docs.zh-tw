---
title: "靜態程式庫 (C + + /CX) |Microsoft 文件"
ms.custom: 
ms.date: 02/03/2017
ms.prod: windows-client-threshold
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
caps.latest.revision: "10"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a68475447ed520298b0eab7949386c2e8d078ac6
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="static-libraries-ccx"></a>靜態程式庫 (C++/CX)
在通用 Windows 平台應用程式中使用的靜態程式庫可包含 ISO 標準 c + + 程式碼，包括 STL 型別，以及未從通用 Windows 平台應用程式平台排除的 Win32 Api 呼叫。 靜態程式庫會使用 Windows 執行階段元件，並可能會建立 Windows 執行階段元件特定限制。  
  
## <a name="creating-static-libraries"></a>建立靜態程式庫  
  
#### <a name="to-create-a-static-library-for-use-in-a-universal-windows-platform-app"></a>若要建立通用 Windows 平台應用程式中使用靜態程式庫  
  
1.  在功能表列上選擇 **檔案** > **新增** > **專案** > **空白靜態程式庫**適用於通用 Windows 平台應用程式。  
  
2.  在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **屬性**]。 在**屬性**對話方塊**組態屬性** > **一般**頁面上，設定為通用 Windows 平台應用程式支援**[是]**。  
  
3.  在**組態屬性** > **C/c + +**頁面上，設定**取用**Windows 執行階段**延伸**至**是 (/ZW)**。  
  
 當您編譯新的靜態程式庫中，如果您針對通用 Windows 平台應用程式中排除的 Win32 api 呼叫時，編譯器將會引發錯誤 c3861: 「 找不到識別項 」。 若要尋找支援為 Windows 執行階段的替代方法，請參閱[Windows 市集應用程式中的 Windows Api 替代方案](http://msdn.microsoft.com/en-us/75568012-61e0-41cc-a4df-c698f54f21ec)。  
  
 如果您將 c + + 靜態程式庫專案加入至通用 Windows 平台應用程式方案時，您可能必須更新程式庫專案的屬性設定，讓通用 Windows 平台支援屬性設為**是**。 若未進行此設定，程式碼仍會建置並連結，但在您嘗試驗證 [!INCLUDE[win8_appstore_long](../cppcx/includes/win8-appstore-long-md.md)]的應用程式時將會發生錯誤。 靜態程式庫必須以使用它的專案相同的編譯器設定進行編譯。  
  
 如果您使用會建立公用 `ref` 類別、公用介面類別或公用實值類別的靜態程式庫，連結器將會引發下列警告：  
  
> **警告 LNK4264:** ，撰寫 Windows 執行階段型別時不建議與包含 Windows 執行階段中繼資料的靜態程式庫連結至靜態程式庫，以 /ZW 編譯的目的檔封存附註。  
  
 只有當靜態程式庫不會產生在程式庫本身以外使用的 Windows 執行階段元件，您可以放心忽略此警告。 如果程式庫不會使用它所定義的元件，則連結器最佳化會將實作去除，即使公用中繼資料包含型別資訊。 這表示靜態程式庫中的公用元件會進行編譯，但不會在執行階段啟動。 基於這個理由，必須在動態連結程式庫 (DLL) 中實作 Windows 執行階段的任何元件預定由其他元件或應用程式。  
  
## <a name="see-also"></a>請參閱  
 [執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md)