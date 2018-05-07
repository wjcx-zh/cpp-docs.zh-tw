---
title: 如何： 建立可驗證的 c + + 專案 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- verifiable assemblies [C++], creating
- conversions, C++ projects
- Visual C++ projects
ms.assetid: 4ef2cc1a-e3e5-4d67-8d8d-9c614f8ec5d3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a012e52a8eb825c3ffc6b694c888cef8a174f37e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-verifiable-c-projects-ccli"></a>如何：建立可驗證的 C++ 專案 (C++/CLI)
Visual c + + 應用程式精靈不會建立驗證專案中，但是專案可以轉換為可驗證。 本主題描述如何設定專案屬性和修改專案來轉換您的 Visual c + + 專案，以產生可驗證的應用程式的原始程式檔。  
  
## <a name="compiler-and-linker-settings"></a>編譯器和連結器設定  
 根據預設，.NET 專案使用 /clr 編譯器旗標，並設定連結器，以目標為 x86 硬體。 可驗證的程式碼，您必須使用 /clr: safe 旗標，而且您必須指示連結器產生 MSIL，而不是原生機器指令。  
  
#### <a name="to-change-the-compiler-and-linker-settings"></a>若要變更的編譯器和連結器設定  
  
1.  顯示專案屬性頁。 如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
2.  在**一般**頁面**組態屬性** 節點，設定**Common Language Runtime 支援**屬性**安全 MSIL Common Language執行階段支援 (/: safe)**。  
  
3.  在**進階**頁面**連結器** 節點，設定**CLR 映像類型**屬性**強制安全 IL 映像 (/ /clrimagetype: safe)**。  
  
## <a name="removing-native-data-types"></a>移除原生資料類型  
 因為原生資料型別非驗證的即使實際上使用，您必須移除所有標頭檔包含原生類型。  
  
> [!NOTE]
>  下列程序適用於 Windows Forms 應用程式 (.NET) 及主控台應用程式 (.NET) 的專案。  
  
#### <a name="to-remove-references-to-native-data-types"></a>若要移除原生資料類型的參考  
  
1.  標記為註解 Stdafx.h 檔案中的所有項目。  
  
## <a name="configuring-an-entry-point"></a>設定進入點  
 可驗證的應用程式無法使用 C 執行階段程式庫 (CRT)，因為它們不能相依於 CRT 呼叫為標準的進入點的主要功能。 這表示，您必須明確地提供給連結器一開始呼叫函式名稱。 （在此情況下，而不是 main （） 或 _tmain() 用 main （） 來表示非 CRT 進入點，但必須明確指定的進入點，因為此名稱可自行決定）。  
  
> [!NOTE]
>  下列程序套用至主控台應用程式 (.NET) 專案。  
  
#### <a name="to-configure-an-entry-point"></a>若要設定的進入點  
  
1.  _Tmain() 改在專案的主要.cpp 檔案中的 main （）。  
  
2.  顯示專案屬性頁。 如需詳細資訊，請參閱[使用專案屬性](../ide/working-with-project-properties.md)。  
  
3.  在**進階**頁面**連結器**節點中，輸入`Main`為**進入點**屬性值。  
  
## <a name="see-also"></a>另請參閱  
 [純粹的和可驗證的程式碼 (C++/CLI)](../dotnet/pure-and-verifiable-code-cpp-cli.md)