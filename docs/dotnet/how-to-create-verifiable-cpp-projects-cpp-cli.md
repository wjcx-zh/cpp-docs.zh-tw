---
title: HOW TO：建立可驗證的 c + + 專案 (C + + /cli CLI)
ms.date: 11/04/2016
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
ms.openlocfilehash: de3742717bf55c53ab4007aaed18b6ce687fbede
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57817371"
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>如何： 建立可驗證的 c + + 專案 (C + + /cli CLI)

Visual c + + 應用程式精靈不會建立可驗證的專案。

> [!IMPORTANT]
> 已被取代的 visual Studio 2015 和 Visual Studio 2017 不支援 **/clr: pure**並 **/clr: safe**建立可驗證的專案。 如果您需要可驗證程式碼，我們建議您將轉譯成 C# 程式碼。

不過，如果您使用較舊版本的 Visual c + + 編譯器工具組支援 **/clr: pure**並 **/clr: safe**，專案可以將其轉換為可驗證。 本主題描述如何設定專案屬性並修改專案來轉換您的 Visual c + + 專案，以產生可驗證的應用程式的原始程式檔。

## <a name="compiler-and-linker-settings"></a>編譯器和連結器設定

根據預設，.NET 專案使用 /clr 編譯器旗標，並設定目標 x86 硬體連結器。 可驗證的程式碼，您必須使用 /clr: safe 旗標，而且您必須指示連結器產生的 MSIL，而不是原生機器指令。

### <a name="to-change-the-compiler-and-linker-settings"></a>若要變更的編譯器和連結器設定

1. 顯示專案屬性頁。 如需詳細資訊，請參閱 <<c0> [ 設定編譯器和組建屬性](../build/working-with-project-properties.md)。

1. 在上**一般**頁面**組態屬性**節點，設定**Common Language Runtime 支援**屬性設**安全 MSIL Common Language執行階段支援 (/: safe)**。

1. 在上**進階**頁面**連結器**節點，設定**CLR 映像類型**屬性設**強制安全 IL 映像 (/ /clrimagetype: safe)**。

## <a name="removing-native-data-types"></a>移除原生資料類型

因為原生資料類型非驗證的即使實際上使用，您必須移除所有標頭檔包含原生型別。

> [!NOTE]
> 下列程序適用於 Windows Forms 應用程式 (.NET) 和主控台應用程式 (.NET) 的專案。

### <a name="to-remove-references-to-native-data-types"></a>若要移除原生資料類型的參考

1. 標記為註解 Stdafx.h 檔案中的所有項目。

## <a name="configuring-an-entry-point"></a>設定進入點

可驗證的應用程式無法使用 C 執行階段程式庫 (CRT)，因為它們不能相依於 CRT 呼叫 main 函式的標準的進入點。 這表示您必須明確地提供給連結器一開始要呼叫的函式的名稱。 （在本例中，main （） 而不是 main （） 或 _tmain() 用來表示非 CRT 進入點，但此名稱必須明確指定的進入點，因為是任意的）。

> [!NOTE]
> 下列程序適用於主控台應用程式 (.NET) 專案。

#### <a name="to-configure-an-entry-point"></a>若要設定的進入點

1. 將 _tmain() 變更專案的主要.cpp 檔案中的 main （）。

1. 顯示專案屬性頁。 如需詳細資訊，請參閱 <<c0> [ 設定編譯器和組建屬性](../build/working-with-project-properties.md)。

1. 在上**進階**頁面**連結器**節點中，輸入`Main`作為**進入點**屬性值。

## <a name="see-also"></a>另請參閱

- [純粹的和可驗證的程式碼 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)
