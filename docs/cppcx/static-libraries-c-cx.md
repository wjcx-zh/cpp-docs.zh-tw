---
title: 靜態程式庫 (C + + /CX) |Microsoft Docs
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 7faf53c8-fa21-42cc-8246-d32533ef9dfa
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5bb69b65d78b6369d872fd6f953f6ddde382c21b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2018
ms.locfileid: "42602285"
---
# <a name="static-libraries-ccx"></a>靜態程式庫 (C++/CX)
通用 Windows 平台 (UWP) 應用程式中使用的靜態程式庫可以包含 ISO 標準 c + + 程式碼，包括 STL 型別，以及不會從 Windows 執行階段應用程式平台排除的 Win32 Api 呼叫。 靜態程式庫會使用 Windows 執行階段元件，並可能會建立 Windows 執行階段元件，但有某些限制。  
  
## <a name="creating-static-libraries"></a>建立靜態程式庫  
  
#### <a name="to-create-a-static-library-for-use-in-a-uwp-app"></a>若要建立靜態程式庫用於 UWP 應用程式中  
  
1.  在功能表列上，選擇 [檔案] > [新增] > [專案]。 底下**Visual c + +** > **Windows Universal**選擇**靜態程式庫 (通用 Windows)**。  
  
2.  在 [ **方案總管**] 中，開啟專案的捷徑功能表，然後選擇 [ **屬性**]。 在 **屬性**對話方塊的 **組態屬性** > **C/c + +** 頁面上，設定**使用 Windows 執行階段延伸模組**要**是 (/ZW)**。  
  
 當您編譯新的靜態程式庫中，如果您排除於 UWP 應用程式的 Win32 api 呼叫時，編譯器將會引發錯誤 c3861: 「 找不到識別項 」。 若要尋找支援的 Windows 執行階段的替代方法，請參閱[UWP 應用程式中的 Windows Api 替代方案](/uwp/win32-and-com/alternatives-to-windows-apis-uwp)。  
  
 如果您將 c + + 靜態程式庫專案加入 UWP 應用程式方案時，您可能必須更新程式庫專案的屬性設定，讓 UWP 支援屬性設定為**是**。 如果沒有此設定中，程式碼會建立，並連結，但錯誤發生於您嘗試確認 Microsoft Store 應用程式。 靜態程式庫必須以使用它的專案相同的編譯器設定進行編譯。  
  
 如果您使用會建立公用 `ref` 類別、公用介面類別或公用實值類別的靜態程式庫，連結器將會引發下列警告：  
  
> **警告 LNK4264:** 封存至靜態程式庫，以 /ZW 編譯的物件檔案請注意，撰寫 Windows 執行階段型別時不建議將包含 Windows 執行階段中繼資料的靜態程式庫連結。  
  
 靜態程式庫未產生會在程式庫本身以外使用的 Windows 執行階段元件時，才，您可以放心地忽略警告。 如果程式庫不會使用它所定義的元件，則連結器最佳化會將實作去除，即使公用中繼資料包含型別資訊。 這表示靜態程式庫中的公用元件會進行編譯，但不會在執行階段啟動。 基於這個理由，由其他元件或應用程式是供取用任何 Windows 執行階段元件必須實作的動態連結程式庫 (DLL) 中。  
  
## <a name="see-also"></a>另請參閱  
 [執行緒和封送處理](../cppcx/threading-and-marshaling-c-cx.md)