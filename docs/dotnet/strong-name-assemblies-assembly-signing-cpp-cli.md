---
title: 強式名稱組件 （組件簽署） (C + + /cli CLI) |Microsoft Docs
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
ms.openlocfilehash: 75b7df96b9366680b69d40dea866fb3067a507b7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430900"
---
# <a name="strong-name-assemblies-assembly-signing-ccli"></a>強式名稱組件 (組件簽署) (C++/CLI)

本主題討論如何登入您的組件，通常是指讓您的組件強式名稱。

## <a name="remarks"></a>備註

Visual c + + 時，請登入您的組件，以避免發生與 CLR 屬性，以簽署組件相關的問題使用連結器選項：

- <xref:System.Reflection.AssemblyDelaySignAttribute>

- <xref:System.Reflection.AssemblyKeyFileAttribute>

- <xref:System.Reflection.AssemblyKeyNameAttribute>

不使用屬性的原因包括索引鍵的名稱會顯示在組件中繼資料，可能會有安全性風險，如果檔案名稱中包含機密資訊的事實。 此外，Visual c + + 開發環境所使用的建置程序將會失效，如果您使用 CLR 屬性來指定組件的強式的名稱，並接著執行組件上的 後置處理 mt.exe 等工具，已簽署組件的索引鍵。

如果您在命令列建置，使用連結器選項來簽署組件，然後再執行 後置處理工具 （mt.exe)，您必須重新簽署組件使用 sn.exe。 或者，您可以建置和延遲簽署組件並執行後置處理的工具之後, 再完成簽署。

如果在開發環境中建置時，您會使用簽署的屬性，您可以成功登入的組件藉由明確呼叫 sn.exe ([Sn.exe （強式名稱工具）](/dotnet/framework/tools/sn-exe-strong-name-tool)) 在 建置後事件。 如需詳細資訊，請參閱[指定建置事件](../ide/specifying-build-events.md)。 如果您使用屬性和建置後事件，相較於使用連結器選項，建置時間可能較少。

下列連結器選項支援簽署的組件：

- [/DELAYSIGN (部分簽署組件)](../build/reference/delaysign-partially-sign-an-assembly.md)

- [/KEYFILE (指定金鑰或金鑰組以簽署組件)](../build/reference/keyfile-specify-key-or-key-pair-to-sign-an-assembly.md)

- [/KEYCONTAINER (指定金鑰容器以簽署組件)](../build/reference/keycontainer-specify-a-key-container-to-sign-an-assembly.md)

如需有關強式的組件的詳細資訊，請參閱 <<c0> [ 建立和使用強式名稱組件](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies)。

## <a name="see-also"></a>另請參閱

[以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)