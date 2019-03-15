---
title: /CLRUNMANAGEDCODECHECK (Remove SuppressUnmanagedCodeSecurityAttribute)
ms.date: 09/27/2018
ms.topic: reference
f1_keywords:
- /CLRUNMANAGEDCODECHECK
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
author: corob-msft
ms.author: corob
ms.openlocfilehash: cb23106648e3325755a857d0b962112e9bdcfac4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822596"
---
# <a name="clrunmanagedcodecheck-remove-suppressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (Remove SuppressUnmanagedCodeSecurityAttribute)

**/CLRUNMANAGEDCODECHECK**指定連結器不會套用<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>至連結器產生`PInvoke`從 managed 程式碼呼叫原生 Dll。

## <a name="syntax"></a>語法

> **/CLRUNMANAGEDCODECHECK**[**:NO**]

## <a name="remarks"></a>備註

根據預設，連結器適用於**SuppressUnmanagedCodeSecurityAttribute**至連結器產生`PInvoke`呼叫。 當 **/CLRUNMANAGEDCODECHECK**生效時， **SuppressUnmanagedCodeSecurityAttribute**已移除。 若要明確套用**SuppressUnmanagedCodeSecurityAttribute**至連結器產生`PInvoke`呼叫，您可以使用 **/CLRUNMANAGEDCODECHECK:NO**。

連結器只會將屬性加入至使用編譯的物件 **/clr**或是 **/clr: pure**。 不過， **/clr: pure**編譯器選項是在 Visual Studio 2015 中已被取代，不支援的 Visual Studio 2017 中。

A`PInvoke`呼叫時，所產生連結器連結器找不到受管理的符號，以滿足 managed 呼叫端的參考，但是可以找到原生的符號，來滿足該參考。 如需詳細資訊`PInvoke`，請參閱 <<c2> [ 從 Managed 程式碼呼叫原生函數](../../dotnet/calling-native-functions-from-managed-code.md)。

請注意，如果您使用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>在您的程式碼中，您應該明確設定 **/CLRUNMANAGEDCODECHECK**移除**SuppressUnmanagedCodeSecurity**屬性。 如果映像同時包含是潛在的安全性弱點**SuppressUnmanagedCodeSecurity**並**AllowPartiallyTrustedCallers**屬性。

請參閱[Unmanaged 程式碼的安全程式碼撰寫指導方針](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code)如需有關使用的含意**SuppressUnmanagedCodeSecurityAttribute**。

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項

1. 開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱 <<c0> [ 在 Visual Studio 中的設定 c + + 編譯器和組建屬性](../working-with-project-properties.md)。

1. 展開 [組態屬性] 節點。

1. 依序展開**連結器**節點。

1. 選取 **進階**屬性頁。

1. 修改**CLR 未受管理的程式碼檢查**屬性。

### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項

1. 請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>。

## <a name="see-also"></a>另請參閱

- [MSVC 連結器參考](linking.md)
- [MSVC 連結器選項](linker-options.md)
