---
title: "如何： 移轉至 clr: pure (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- /clr compiler option [C++], migrating to /clr:pure
- migration [C++], pure MSIL
- pure MSIL [C++], porting to
ms.assetid: 5ffb1184-2095-4ade-84aa-4fa6324bc764
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b8d49ee233167c02570408ba091c2a99b78487d5
ms.sourcegitcommit: fa7a6dccddce3747389c91277a53e296f905305c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/14/2018
---
# <a name="how-to-migrate-to-clrpure-ccli"></a>如何：移轉至 /clr:pure (C++/CLI)
本主題討論問題可能會發生移轉到使用純的 MSIL 時**/clr: pure** (請參閱[/clr （Common Language Runtime 編譯）](../build/reference/clr-common-language-runtime-compilation.md)如需詳細資訊)。 本主題假設程式碼移轉目前編譯為使用混合的組件**/clr**選項，因為純的 MSIL 從 unmanaged 程式碼的移轉路徑不是直接的工作。 Unmanaged 程式碼，請參閱[How to： 移轉至 /clr](../dotnet/how-to-migrate-to-clr.md)然後再嘗試將移轉至純的 MSIL。  
  
## <a name="basic-changes"></a>基本的變更  
 純的 MSIL 被組成 MSIL 指令，因此含有無法以 MSIL 表示的函式的程式碼會導致編譯。 這包括函式定義為使用不呼叫慣例[__clrcall](../cpp/clrcall.md)。 （非 __clrcall 函式可以叫用純的 MSIL 元件，但未定義。）  
  
 若要確保沒有執行階段錯誤，您應該啟用 C4412 警告。 加入啟用 C4412`#pragma warning (default : 4412)`到您使用編譯每個編譯單位**/clr: pure**和 c + + 類型 IJW 來回傳遞之 (**/clr)**或原生程式碼。 請參閱[編譯器警告 （層級 2） C4412](../error-messages/compiler-warnings/compiler-warning-level-2-c4412.md)如需詳細資訊。  
  
## <a name="architectural-considerations"></a>架構上的考量  
 某些純的 MSIL 組件中所列的限制[純粹的和可驗證程式碼 (C + + CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)有個應用程式的設計和移轉策略的高層級含意。 最值得注意的是，與混合的組件不同的是純 MSIL 組件不喜歡與未受管理的模組完全相容。  
  
 純的 MSIL 組件可以呼叫 unmanaged 函式，但是無法由 unmanaged 函式呼叫。 如此一來，純的 MSIL 是更好的候選項目，比伺服端程式碼，以供 unmanaged 函式會使用 unmanaged 函式的用戶端程式碼。 如果純的 MSIL 組件中包含的功能，以供 unmanaged 函式必須使用混合的組件做為介面層。  
  
 使用 ATL 或 MFC 應用程式不適合用來移轉到純的 MSIL，因為這個版本不支援這些程式庫。 同樣地，[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]包含不在編譯的標頭檔**/clr: pure**。  
  
 雖然純的 MSIL 組件可以呼叫 unmanaged 函式，這項功能是限制為簡單的 C 樣式函式。 更複雜的 unmanaged Api 的使用是可能需要公開的 COM 介面或混合的組件可以做為純的 MSIL 和 unmanaged 的元件之間介面的表單中未受管理的功能。 使用混合的組件層級是使用不接受回呼函式，例如，unmanaged 函式，因為純的組件是無法用來做回呼提供原生呼叫的函式的唯一方式。  
  
## <a name="application-domains-and-calling-conventions"></a>應用程式定義域和呼叫慣例  
 雖然您可以針對純的 MSIL 組件使用未受管理的功能，函式和靜態資料的處理方式不同。 純的組件中函式的實作與[__clrcall](../cpp/clrcall.md)呼叫慣例和靜態資料會儲存每個應用程式定義域。 這不同於預設值為未受管理和混合的組件，使用[__cdecl](../cpp/cdecl.md)函式的呼叫慣例和儲存靜態資料，每個處理程序為基礎。  
  
 純的 MSIL （和可驗證以 /clr: safe 編譯的程式碼） 的內容中，這些預設值是透明的做為[__clrcall](../cpp/clrcall.md) CLR 的預設呼叫慣例，而且應用程式定義域的原生靜態範圍，.NET 應用程式中的全域資料。 不過，當遇到 unmanaged 或混合的元件，函式和全域資料的不同處理方式可能會造成問題。  
  
 比方說，如果純的 MSIL 元件，unmanaged 或混合 DLL 中呼叫函式之 DLL 的標頭檔用以編譯純粹組件。 不過，除非已明確指出標頭中的每個函式的呼叫慣例，否則它們將全部假設為[__clrcall](../cpp/clrcall.md)。 這稍後會導致執行階段失敗，因為這些函式可能使用實作[__cdecl](../cpp/cdecl.md)慣例。 未受管理的標頭檔中的函式明確標示為[__cdecl](../cpp/cdecl.md)，或必須在重新編譯整個 DLL 原始程式碼**/clr: pure**。  
  
 同樣地，假設函式指標指向[__clrcall](../cpp/clrcall.md)函式下**/clr: pure**編譯。 這些太必須明確標註具有正確的呼叫慣例。  
  
 如需詳細資訊，請參閱[應用程式定義域和 Visual c + +](../dotnet/application-domains-and-visual-cpp.md)。  
  
## <a name="linking-limitations"></a>連結的限制  
 Visual c + + 連結器不會嘗試連線混合或純 OBJ 檔案，因為不同的儲存體的範圍和呼叫慣例。  
  
## <a name="see-also"></a>請參閱  
 [純粹的和可驗證的程式碼 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)