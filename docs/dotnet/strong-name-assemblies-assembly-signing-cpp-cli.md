---
title: 強式名稱組件 （組件簽署） (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- assemblies [C++]
- signing assemblies
- .NET Framework [C++], assembly signing
- assemblies [C++], signing
- linker [C++], assembly signing
- strong-named assemblies [C++]
ms.assetid: c337cd3f-e5dd-4c6f-a1ad-437e85dba1cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5d7ae911d2572a35ee8dbb21d5484b4679b64c4d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33169188"
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>強式名稱組件 (組件簽署) (C++/CLI)
本主題討論如何登入您的組件，通常稱為賦予您的組件強式名稱。  
  
## <a name="remarks"></a>備註  
 當使用 Visual c + +，使用連結器選項來簽署組件，以避免與 CLR 屬性，以簽署組件相關的問題：  
  
-   <xref:System.Reflection.AssemblyDelaySignAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyFileAttribute>  
  
-   <xref:System.Reflection.AssemblyKeyNameAttribute>  
  
 不使用屬性的原因包括索引鍵的名稱會出現在組件中繼資料，可能會有安全性風險，如果檔案名稱中包含機密資訊的事實。 此外，使用 Visual c + + 開發環境的建置程序會導致無效的索引鍵，如果您使用 CLR 屬性，來為組件提供強式名稱，然後執行組件上的 後置處理這類工具 mt.exe，組件簽署的。  
  
 如果您在命令列建置，用以簽署組件連結器選項，然後再執行後置處理這類工具 （mt.exe)，您必須重新簽署組件使用 sn.exe。 或者，您可以建置並延遲簽署組件以及之後執行後置處理的工具，就可以完成的簽章。  
  
 如果您使用的簽章的屬性，在開發環境中建置時，您可以藉由明確地呼叫 sn.exe 成功簽署組件 ([Sn.exe （強式名稱工具）](/dotnet/framework/tools/sn-exe-strong-name-tool)) 中建置後事件。 如需詳細資訊，請參閱[指定建置事件](../ide/specifying-build-events.md)。 如果您使用屬性和建置後事件，相較於使用連結器選項，建置時間可能小於。  
  
 下列連結器選項支援簽署的組件：  
  
-   [/DELAYSIGN (部分簽署組件)](../build/reference/delaysign-partially-sign-an-assembly.md)  
  
-   [/KEYFILE (指定金鑰或金鑰組以簽署組件)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)  
  
-   [/KEYCONTAINER (指定金鑰容器以簽署組件)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)  
  
 如需有關強式組件的詳細資訊，請參閱[Creating and using strong-named Assemblies](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)。  
  
## <a name="see-also"></a>另請參閱  
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)