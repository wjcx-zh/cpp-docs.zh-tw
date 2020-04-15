---
title: 如何:建立部分受信任的應用程式(C++/CLI)
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
ms.openlocfilehash: 9df3a751f4073472b9495425599aaf43878db99a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364395"
---
# <a name="how-to-create-a-partially-trusted-application-by-removing-dependency-on-the-crt-library-dll"></a>如何：移除 CRT 程式庫 DLL 的相依性以建立部分信任的應用程式

本主題討論如何通過刪除對 msvcm90.dll 的依賴項,使用 Visual C++創建部分受信任的通用語言運行時應用程式。

使用 **/clr**構建的可視C++應用程式將依賴於 msvcm90.dll,msvcm90.dll 是 C-執行時庫的一部分。 當您希望應用程式在部分信任環境中使用時,CLR將在 DLL 上強制實施某些代碼訪問安全規則。 因此,有必要刪除此依賴項,因為msvcm90.dll包含本機代碼,並且無法對它強制實施代碼存取安全策略。

如果應用程式不使用 C-Runtime 庫的任何功能,並且希望從代碼中刪除對此庫的依賴項,則必須使用 **/NODEFAULTLIB:msvcmrt.lib**連結器選項並與 ptrustm.lib 或 ptrustmd.lib 連結。 這些庫包含用於應用程式初始化和非初始化的物件檔、初始化代碼使用的異常類以及託管異常處理代碼。 在這些庫中連結將刪除對msvcm90.dll的任何依賴。

> [!NOTE]
> 對於使用 ptrust 庫的應用程式,程式集取消初始化的順序可能不同。 對於普通應用程式,程式集通常按載入程式集的相反順序卸載,但這不能保證。 對於部分信任應用程式,程式集的卸載順序通常與載入程式集的順序相同。 這也不能保證這一點。

### <a name="to-create-a-partially-trusted-mixed-clr-application"></a>建立部分受信任的混合 (/clr) 應用程式

1. 要刪除對 msvcm90.dll 的依賴項,必須指定連結器不要使用 **/NODEFAULTLIB:msvcmrt.lib**連結器選項來包括此庫。 有關如何使用可視化工作室開發環境或以程式設計方式執行此操作的資訊,請參閱[/NODEFAULTLIB(忽略庫)。](../build/reference/nodefaultlib-ignore-libraries.md)

1. 將其中一個 ptrustm 庫添加到連結器輸入依賴項。 如果要在發佈模式下構建應用程式,請使用 ptrustm.lib。 對於調試模式,請使用 ptrustmd.lib。 有關如何使用 Visual Studio 開發環境或以程式設計方式執行此操作的資訊,請參閱[。Lib 檔案作為連結器輸入](../build/reference/dot-lib-files-as-linker-input.md)。

## <a name="see-also"></a>另請參閱

[混合 (原生和 Managed) 組件](../dotnet/mixed-native-and-managed-assemblies.md)<br/>
[混合程式集的初始化](../dotnet/initialization-of-mixed-assemblies.md)<br/>
[混合組件的程式庫支援](../dotnet/library-support-for-mixed-assemblies.md)<br/>
[/link (傳遞選項給連結器)](../build/reference/link-pass-options-to-linker.md)
