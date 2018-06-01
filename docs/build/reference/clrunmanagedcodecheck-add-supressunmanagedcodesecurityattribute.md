---
title: /CLRUNMANAGEDCODECHECK （加入 SupressUnmanagedCodeSecurityAttribute） |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
dev_langs:
- C++
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9d0a70ea74851d3a10f9d46b8289098d6fb3fe22
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/01/2018
ms.locfileid: "34705370"
---
# <a name="clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (加入 SupressUnmanagedCodeSecurityAttribute)

**/CLRUNMANAGEDCODECHECK**指定連結器是否將套用<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>至連結器產生`PInvoke`從 managed 程式碼呼叫原生 Dll。

## <a name="syntax"></a>語法

> **/CLRUNMANAGEDCODECHECK**[**: NO**]

## <a name="remarks"></a>備註

根據預設，連結器適用於**SuppressUnmanagedCodeSecurityAttribute**至連結器產生`PInvoke`呼叫。 當 **/CLRUNMANAGEDCODECHECK**作用中， **SuppressUnmanagedCodeSecurityAttribute**未套用。

連結器只會將屬性加入至使用編譯的物件 **/clr**或 **/clr: pure**。 不過， **/clr: pure**編譯器選項已被取代 Visual Studio 2015 中，在 Visual Studio 2017 中支援。

A`PInvoke`呼叫時，所產生連結器連結器找不到受管理的符號，來滿足 managed 呼叫端的參考，但是可以找到滿足該參考的原生符號。 如需有關`PInvoke`，請參閱[從 Managed 程式碼呼叫原生函式](../../dotnet/calling-native-functions-from-managed-code.md)。

請注意，如果您使用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>在程式碼中，您應該明確設定 **/CLRUNMANAGEDCODECHECK**。 它是潛在的安全性弱點，如果映像包含 SuppressUnmanagedCodeSecurity 和 AllowPartiallyTrustedCallers 屬性。

請參閱[Unmanaged 程式碼的安全程式碼撰寫指導方針](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code)如需有關使用的含意**SuppressUnmanagedCodeSecurityAttribute**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。

1. 展開**組態屬性**節點。

1. 展開**連結器**節點。

1. 選取**進階**屬性頁。

1. 修改**CLR Unmanaged 的程式碼檢查**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>。

## <a name="see-also"></a>另請參閱

- [設定連結器選項](../../build/reference/setting-linker-options.md)
- [連結器選項](../../build/reference/linker-options.md)
