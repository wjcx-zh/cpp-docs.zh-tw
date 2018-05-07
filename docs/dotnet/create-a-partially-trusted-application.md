---
title: 如何： 建立部分信任的應用程式 (C + + /CLI) |Microsoft 文件
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: a4a0a4b8b1045a9107158c6e67ecdfa7939b6a08
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>如何：移除 CRT 程式庫 DLL 的相依性以建立部分信任的應用程式
本主題討論如何建立使用 Visual c + + 所移除的相依性 msvcm90.dll 部分信任的 Common Language Runtime 應用程式。  
  
 建置的 Visual c + + 應用程式 **/clr** msvcm90.dll，這是 C 執行階段程式庫的一部分會具有相依性。 當您想用於部分信任環境中的應用程式時，CLR 會強制執行您的 DLL 上特定程式碼存取安全性規則。 因此，它必須移除此依存性，因為 msvcm90.dll 包含原生程式碼，而且無法在其上強制執行程式碼存取安全性原則。  
  
 如果您的應用程式不使用 C 執行階段程式庫的任何功能，而且您想要從您的程式碼中移除對此文件庫的相依性，您必須使用 **/NODEFAULTLIB:msvcmrt.lib**連結器選項和連結ptrustm.lib 或 ptrustmd.lib。 這些程式庫包含初始設定和應用程式的未初始化的物件檔，例外狀況類別初始化程式碼中，使用 managed 例外狀況處理程式碼。 在這些程式庫的其中一個連結，將會移除 msvcm90.dll 上的任何相依性。  
  
> [!NOTE]
>  組件未初始化的順序可能會與不同的應用程式，使用 ptrust 程式庫。 對於一般應用程式，組件的卸載通常中載入，但這不保證的反向順序。 對於部分信任應用程式中，組件的卸載通常已載入的順序相同。 這樣一來，此外，我們無法保證。  
  
### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>若要建立部分信任混合 (/ clr) 應用程式  
  
1.  若要移除對 msvcm90.dll 的相依性，您必須指定至連結器不包含此程式庫使用 **/NODEFAULTLIB:msvcmrt.lib**連結器選項。 如需有關如何使用 Visual Studio 開發環境執行此動作，或以程式設計的方式，請參閱詳細[/NODEFAULTLIB （忽略程式庫）](../build/reference/nodefaultlib-ignore-libraries.md)。  
  
2.  將其中一個 ptrustm 程式庫加入至連結器輸入相依性。 如果您要建置您的應用程式，在發行模式中，請使用 ptrustm.lib。 偵錯模式中，使用 ptrustmd.lib。 如需有關如何使用 Visual Studio 開發環境執行此動作，或以程式設計的方式，請參閱詳細[。Lib 檔案做為連結器輸入](../build/reference/dot-lib-files-as-linker-input.md)。  
  
## <a name="see-also"></a>另請參閱  
 [混合 （原生和 Managed） 組件](../dotnet/mixed-native-and-managed-assemblies.md)   
 [混合的組件的初始化](../dotnet/initialization-of-mixed-assemblies.md)   
 [混合的組件的程式庫支援](../dotnet/library-support-for-mixed-assemblies.md)   
 [/link (傳遞選項給連結器)](../build/reference/link-pass-options-to-linker.md)   
