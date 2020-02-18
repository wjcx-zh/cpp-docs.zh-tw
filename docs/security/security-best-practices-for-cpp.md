---
title: C++ 的安全性最佳做法
ms.date: 05/08/2018
f1_keywords:
- securitybestpracticesVC
helpviewer_keywords:
- Visual C++, security
- security [C++]
- security [C++], best practices
ms.assetid: 86acaccf-cdb4-4517-bd58-553618e3ec42
ms.openlocfilehash: eaaa581ff622438c2e395c34b4b026aca693a845
ms.sourcegitcommit: 7bea0420d0e476287641edeb33a9d5689a98cb98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/17/2020
ms.locfileid: "77416159"
---
# <a name="security-best-practices-for-c"></a>C++ 的安全性最佳做法

本文包含安全性工具和作法的相關資訊。 使用它們不會讓應用程式免受攻擊，但是可能可以減少成功的攻擊。

## <a name="visual-c-security-features"></a>Visual C++ 安全性功能

這些安全性功能內建于 Microsoft C++編譯器和連結器：

[/guard (啟用控制流程防護)](../build/reference/guard-enable-control-flow-guard.md)<br/>
讓編譯器在編譯階段分析間接呼叫目標的控制流程，然後插入程式碼以在執行時間確認目標。

[/GS (緩衝區安全性檢查)](../build/reference/gs-buffer-security-check.md)<br/>
指示編譯器將滿溢偵測程式碼插入可能有遭利用風險的函式。 偵測到滿溢時，就會停止執行。 預設會開啟這個選項。

[/SAFESEH (映像擁有安全例外狀況處理常式)](../build/reference/safeseh-image-has-safe-exception-handlers.md)<br/>
指示連結器將包含每個例外狀況處理常式位址的資料表併入輸出映像中。 在執行階段，作業系統會使用此資料表，確定只會執行合法的例外狀況處理常式。 這有助於防止惡意攻擊在執行階段所引入的執行例外狀況處理常式。 根據預設，這個選項為關閉狀態。

[/NXCOMPAT](../build/reference/nxcompat.md)、 [/NXCOMPAT （與資料執行防止相容）](../build/reference/nxcompat-compatible-with-data-execution-prevention.md)這些編譯器和連結器選項可啟用資料執行防止（DEP）相容性。 DEP 會保護 CPU 使其不執行非程式碼頁面。

[/analyze (程式碼分析)](../build/reference/analyze-code-analysis.md)<br/>
此編譯器選項會啟動報告潛在安全性問題 (例如緩衝區滿溢、未初始化的記憶體、Null 指標取值以及記憶體流失) 的程式碼分析。 根據預設，這個選項為關閉狀態。 如需詳細資訊，請參閱[C/C++總覽的程式碼分析](/cpp/code-quality/code-analysis-for-c-cpp-overview)。

[/DYNAMICBASE (使用位址空間配置隨機載入)](../build/reference/dynamicbase-use-address-space-layout-randomization.md)<br/>
此連結器選項會建置可執行檔映像，以在開始執行時於記憶體不同位置載入。 此選項也會讓記憶體中的堆疊位置更難預測。

## <a name="security-enhanced-crt"></a>安全性增強 CRT

C 執行階段程式庫 (CRT) 已增強，以包括造成安全性風險之函式的安全版本 (例如，未檢查的 `strcpy` 字串複製函式)。 因為已取代這些函式的較舊不安全版本，所以它們會造成編譯階段警告。 鼓勵您使用這些 CRT 函式的安全版本，而非隱藏編譯警告。 如需詳細資訊，請參閱 [Security Features in the CRT](../c-runtime-library/security-features-in-the-crt.md)。

## <a name="safeint-library"></a>SafeInt 程式庫

[SafeInt 程式庫](../safeint/safeint-library.md)可協助防止整數溢位，以及應用程式執行數學運算時可能會發生的其他可利用的錯誤。 `SafeInt` 程式庫包括[SafeInt 類別](../safeint/safeint-class.md)、 [SafeIntException 類別](../safeint/safeintexception-class.md)和數個[SafeInt 函數](../safeint/safeint-functions.md)。

`SafeInt` 類別可防止整數溢位和除以零惡意探索。 您可以使用它來處理不同類型之值間的比較。 它提供兩個錯誤處理原則。 預設原則可供 `SafeInt` 類別擲回 `SafeIntException` 類別例外狀況，以報告無法完成數學運算的原因。 第二個原則可供 `SafeInt` 類別停止程式執行。 您也可以定義自訂原則。

每個 `SafeInt` 函式都會防止一個數學運算發生可利用的錯誤。 您可以使用兩種不同的參數，而且不需要將它們轉換成相同類型。 若要保護多個數學運算，請使用 `SafeInt` 類別。

## <a name="checked-iterators"></a>已檢查的迭代器

已檢查的迭代器會強制執行容器界限。 根據預設，已檢查的迭代器超出範圍時，會產生例外狀況並結束程式執行。 已檢查的反覆運算器提供其他層級的回應，取決於指派給預處理器定義的值，例如 **\_SECURE\_SCL\_** 會擲回， **\_反覆運算器\_DEBUG\_層級**。 例如，在 **\_反覆運算器\_debug\_LEVEL = 2**時，已檢查的反覆運算器會在「偵測模式」中提供完整的正確性檢查，這些是使用判斷提示所提供的。 如需詳細資訊，請參閱[已檢查的反覆運算](../standard-library/checked-iterators.md)[器和\_ITERATOR\_DEBUG\_層級](../standard-library/iterator-debug-level.md)。

## <a name="code-analysis-for-managed-code"></a>Managed 程式碼的程式碼分析

「Managed 程式碼的程式碼分析」(也稱為 FxCop) 會檢查組件是否符合 .NET Framework 設計方針。 FxCop 會分析每個組件中的程式碼和中繼資料，以檢查下列區域是否有缺失：

- 程式庫設計

- 當地語系化

- 命名慣例

- 效能

- 安全性

## <a name="windows-application-verifier"></a>Windows 應用程式驗證器

[應用程式驗證器（AppVerifier）](/windows-hardware/drivers/debugger/enable-application-verifier)可協助您找出潛在的應用程式相容性、穩定性和安全性問題。

AppVerifier 會監視應用程式使用作業系統的方式。 它會在應用程式執行時監看檔案系統、登錄、記憶體和 API，並建議使用所發現之問題的原始程式碼修正。

您可以使用 AppVerifier：

- 測試常見程式設計錯誤所造成的潛在應用程式相容性錯誤。

- 檢查應用程式是否有記憶體相關問題。

- 找出應用程式中的潛在安全性問題。

## <a name="windows-user-accounts"></a>Windows 使用者帳戶

使用屬於 Administrators 群組的 Windows 使用者帳戶，讓開發人員和客戶暴露在安全性風險下。 如需詳細資訊，請參閱[以使用者群組成員](running-as-a-member-of-the-users-group.md)身分執行和[使用者帳戶控制（UAC）如何影響您的應用程式](how-user-account-control-uac-affects-your-application.md)。

## <a name="guidance-for-speculative-execution-side-channels"></a>推測執行端通道的指引

如需如何識別和緩和軟體中C++的理論式執行端通道硬體弱點的詳細資訊，請參閱[ C++理論式執行端通道的開發人員指引](developer-guidance-speculative-execution.md)。

## <a name="see-also"></a>另請參閱

<xref:System.Security> <br/>
[安全性](/dotnet/standard/security/index)<br/>
[使用者帳戶控制 (UAC) 如何影響應用程式](how-user-account-control-uac-affects-your-application.md)
