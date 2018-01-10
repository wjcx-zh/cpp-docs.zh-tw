---
title: "-CLRUNMANAGEDCODECHECK （加入 SupressUnmanagedCodeSecurityAttribute） |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: /CLRUNMANAGEDCODECHECK
dev_langs: C++
helpviewer_keywords:
- -CLRUNMANAGEDCODECHECK linker option
- /CLRUNMANAGEDCODECHECK linker option
ms.assetid: 73abc426-dab0-45e2-be85-0f9a14206cc2
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b0ac6b7c2c0ba9ea14a2ddd9c227143ec71e2b93
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="clrunmanagedcodecheck-add-supressunmanagedcodesecurityattribute"></a>/CLRUNMANAGEDCODECHECK (加入 SupressUnmanagedCodeSecurityAttribute)
**/CLRUNMANAGEDCODECHECK**指定連結器是否將套用<xref:System.Security.SuppressUnmanagedCodeSecurityAttribute>至連結器產生`PInvoke`從 managed 程式碼呼叫原生 Dll。  
  
## <a name="syntax"></a>語法  
  
```  
/CLRUNMANAGEDCODECHECK[:NO]  
```  
  
## <a name="remarks"></a>備註  
 根據預設，連結器套用 SuppressUnmanagedCodeSecurityAttribute 套用至連結器產生`PInvoke`呼叫。 當**/CLRUNMANAGEDCODECHECK**已生效，不會套用 SuppressUnmanagedCodeSecurityAttribute。  
  
 連結器只會將屬性加入至使用編譯的物件**/clr**或**/clr: pure**。 連結器不會產生`PInvoke`呼叫中使用編譯的物件**/clr: safe**。 如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
 A`PInvoke`呼叫時，所產生連結器連結器找不到受管理的符號，來滿足 managed 呼叫端的參考，但是可以找到滿足該參考的原生符號。 如需有關`PInvoke`，請參閱[從 Managed 程式碼呼叫原生函式](../../dotnet/calling-native-functions-from-managed-code.md)。  
  
 請注意，如果您使用<xref:System.Security.AllowPartiallyTrustedCallersAttribute>在程式碼中，您應該明確設定**/CLRUNMANAGEDCODECHECK**。 它是潛在的安全性弱點，如果映像包含 SuppressUnmanagedCodeSecurity 和 AllowPartiallyTrustedCallers 屬性。  
  
 請參閱[Unmanaged 程式碼的安全程式碼撰寫指導方針](/dotnet/framework/security/secure-coding-guidelines-for-unmanaged-code)如需有關使用 SuppressUnmanagedCodeSecurityAttribute 的含意。  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個連結器選項  
  
1.  開啟專案的 [屬性頁]  對話方塊。 如需詳細資訊，請參閱[使用專案屬性](../../ide/working-with-project-properties.md)。  
  
2.  展開**組態屬性**節點。  
  
3.  展開**連結器**節點。  
  
4.  選取**進階**屬性頁。  
  
5.  修改**CLR Unmanaged 的程式碼檢查**屬性。  
  
### <a name="to-set-this-linker-option-programmatically"></a>若要以程式設計方式設定這個連結器選項  
  
1.  請參閱 <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.CLRUnmanagedCodeCheck%2A>。  
  
## <a name="see-also"></a>請參閱  
 [設定連結器選項](../../build/reference/setting-linker-options.md)   
 [連結器選項](../../build/reference/linker-options.md)