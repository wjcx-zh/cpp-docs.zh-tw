---
title: 如何： 將資料寫入至 Windows 登錄 (C + + /CLI) |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- registry, writing to
- Visual C++, writing to Windows Registry
ms.assetid: 3d40b978-4baa-4779-bfe3-47e2917b757f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 304bc224be8776c9793af07283c6a5697a4e49eb
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33130798"
---
# <a name="how-to-write-data-to-the-windows-registry-ccli"></a>如何：將資料寫入至 Windows 登錄 (C++/CLI)
下列程式碼範例使用<xref:Microsoft.Win32.Registry.CurrentUser>要建立可寫入的執行個體的索引鍵<xref:Microsoft.Win32.RegistryKey>類別對應至**軟體**索引鍵。 <xref:Microsoft.Win32.RegistryKey.CreateSubKey%2A>方法可用來建立新的金鑰和加入 索引鍵/值組。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
// registry_write.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main()  
{  
   // The second OpenSubKey argument indicates that  
   // the subkey should be writable.   
   RegistryKey^ rk;  
   rk  = Registry::CurrentUser->OpenSubKey("Software", true);  
   if (!rk)  
   {  
      Console::WriteLine("Failed to open CurrentUser/Software key");  
      return -1;  
   }  
  
   RegistryKey^ nk = rk->CreateSubKey("NewRegKey");  
   if (!nk)  
   {  
      Console::WriteLine("Failed to create 'NewRegKey'");  
      return -1;  
   }  
  
   String^ newValue = "NewValue";  
   try  
   {  
      nk->SetValue("NewKey", newValue);  
      nk->SetValue("NewKey2", 44);  
   }  
   catch (Exception^)  
   {  
      Console::WriteLine("Failed to set new values in 'NewRegKey'");  
      return -1;  
   }  
  
   Console::WriteLine("New key created.");  
   Console::Write("Use REGEDIT.EXE to verify ");  
   Console::WriteLine("'CURRENTUSER/Software/NewRegKey'\n");  
   return 0;  
}  
```  
  
## <a name="remarks"></a>備註  
 您可以使用.NET Framework 來存取登錄中的以<xref:Microsoft.Win32.Registry>和[RegistryKey](https://msdn.microsoft.com/en-us/library/microsoft.win32.registrykey.aspx)中定義的類別，兩者都<xref:Microsoft.Win32>命名空間。 **登錄**類別是靜態的執行個體的容器<xref:Microsoft.Win32.RegistryKey>類別。 每個執行個體表示登錄根節點。 執行個體<xref:Microsoft.Win32.Registry.ClassesRoot>， <xref:Microsoft.Win32.Registry.CurrentConfig>， <xref:Microsoft.Win32.Registry.CurrentUser>， <xref:Microsoft.Win32.Registry.LocalMachine>，和<xref:Microsoft.Win32.Registry.Users>。  
  
## <a name="see-also"></a>另請參閱  
 [如何： 從 Windows 登錄讀取資料 (C + + /CLI)](../dotnet/how-to-read-data-from-the-windows-registry-cpp-cli.md)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)