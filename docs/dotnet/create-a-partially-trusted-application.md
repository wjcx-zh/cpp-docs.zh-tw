---
title: HOW TO：建立部分信任的應用程式 (C++/CLI)
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- partially trusted applications [C++]
- mixed assemblies [C++], partially trusted applications
- msvcm90[d].dll
- interoperability [C++], partially trusted applications
- interop [C++], partially trusted applications
- /clr compiler option [C++], partially trusted applications
ms.assetid: 4760cd0c-4227-4f23-a7fb-d25b51bf246e
ms.openlocfilehash: afdfb8ca11753d7def9d7da6f431082b1a90c345
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62209118"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>HOW TO：建立部分信任的應用程式移除 CRT 程式庫 DLL 相依性

本主題討論如何建立部分信任的通用語言執行平台應用程式，使用視覺效果C++移除相依性 msvcm90.dll。

視覺效果C++使用所建置的應用程式 **/clr**會將相依性對 msvcm90.dll，也就是 C 執行階段程式庫的一部分。 當您想在部分信任環境中使用您的應用程式時，CLR 會強制執行您的 DLL 上特定程式碼存取安全性規則。 因此，它必須移除此相依性，因為 msvcm90.dll 包含原生程式碼和程式碼存取安全性原則無法強制執行它。

如果您的應用程式不會使用 C 執行階段程式庫的任何功能，而且您想要從您的程式碼中移除此文件庫的相依性，您必須使用 **/NODEFAULTLIB:msvcmrt.lib**連結器選項和連結ptrustm.lib 或 ptrustmd.lib 中。 這些程式庫包含初始設定和應用程式的未初始化的物件檔案，例外狀況類別初始化程式碼中，使用 managed 例外狀況處理程式碼。 在這些程式庫的其中一個連結，將會移除任何相依性 msvcm90.dll。

> [!NOTE]
>  組件未初始化的順序可能會使用 ptrust 程式庫的應用程式不同。 對於一般應用程式，組件的卸載通常會載入它們，但這不保證的反向順序。 對於部分信任應用程式中，組件的卸載通常會載入的順序相同。 如此一來，此外，不保證。

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>若要建立部分信任混合 (/ clr) 的應用程式

1. 若要移除對 msvcm90.dll 的相依性，您必須指定至連結器不要使用包含此程式庫 **/NODEFAULTLIB:msvcmrt.lib**連結器選項。 如需如何使用 Visual Studio 開發環境執行此動作，或以程式設計的方式，請參閱 < [/NODEFAULTLIB (Ignore Libraries)](../build/reference/nodefaultlib-ignore-libraries.md)。

1. 將其中一個 ptrustm 程式庫新增至連結器輸入相依性。 如果您要建置您的應用程式，在發行模式中，請使用 ptrustm.lib。 偵錯模式中，使用 ptrustmd.lib。 如需如何使用 Visual Studio 開發環境執行此動作，或以程式設計的方式，請參閱[。Lib 檔作為連結器輸入](../build/reference/dot-lib-files-as-linker-input.md)。

## <a name="see-also"></a>另請參閱

[混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[混合組件的初始化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[混合組件的程式庫支援](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (傳遞選項給連結器)](../build/reference/link-pass-options-to-linker.md)
