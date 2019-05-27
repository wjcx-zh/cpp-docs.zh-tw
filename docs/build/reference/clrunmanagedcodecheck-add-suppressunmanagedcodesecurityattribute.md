---
title: /CLRUNMANAGEDCODECHECK (移除 SuppressUnmanagedCodeSecurityAttribute)
ms.date: 05/16/2019
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.openlocfilehash: ecc560673a8e98752289ef0e0f89d3abfc1938e4
ms.sourcegitcommit: a10c9390413978d36b8096b684d5ed4cf1553bc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/17/2019
ms.locfileid: "65837246"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (移除 SuppressUnmanagedCodeSecurityAttribute)

**/CLRUNMANAGEDCODECHECK** 會指定連結器不會將 <xref:System.Security.SuppressUnmanagedCodeSecurityAttribute> 套用至連結器產生的 `PInvoke` 呼叫 (從受控程式碼至原生 DLL)。

## <a name="syntax"></a>語法

> **/CLRUNMANAGEDCODECHECK**[**:NO**]

## <a name="remarks"></a>備註

根據預設，連結器會將 **SuppressUnmanagedCodeSecurityAttribute** 套用至連結器產生的 `PInvoke` 呼叫。 當 **/CLRUNMANAGEDCODECHECK** 生效時，即會移除 **SuppressUnmanagedCodeSecurityAttribute**。 若要將 **SuppressUnmanagedCodeSecurityAttribute** 明確套用至連結器產生的 `PInvoke` 呼叫，您可以使用 **/CLRUNMANAGEDCODECHECK:NO**。

連結器只會將屬性新增至使用 **/clr** 或 **/clr:pure** 編譯的物件。 不過，**/clr:pure** 編譯器選項在 Visual Studio 2015 中已被取代，而且無法在 Visual Studio 2017 及更新版本中使用。

當連結器找不到受控符號以滿足受控呼叫端的參考，但可找到滿足該參考的原生符號時，連結器會產生 `PInvoke` 呼叫。 如需 `PInvoke` 的詳細資訊，請參閱[從受控程式碼呼叫原生函式](../../dotnet/calling-native-functions-from-managed-code.md)。

請注意，如果您在程式碼中使用 <xref:System.Security.AllowPartiallyTrustedCallersAttribute>，則應明確設定 **/CLRUNMANAGEDCODECHECK** 以移除 **SuppressUnmanagedCodeSecurity** 屬性。 如果映像中同時包含 **SuppressUnmanagedCodeSecurity** 和 **AllowPartiallyTrustedCallers** 屬性，將是潛在的安全性弱點。

請參閱[受控程式碼的安全編碼指南](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code)，以進一步了解使用 **SuppressUnmanagedCodeSecurityAttribute** 的含意。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資料，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 展開 [連結器] 節點。

1. 選取 [進階] 屬性頁。

1. 修改 [CLR 非受控碼檢查] 屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
