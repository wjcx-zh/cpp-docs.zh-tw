---
title: "如何： 從 Windows 登錄讀取資料 (C + + /CLI) |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- Visual C++, reading from Windows Registry
- registry, reading
ms.assetid: aebf52c0-acc7-40e2-adbc-d34e0a1e467e
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: dfb654ba2cce069086713322624e947e14bc26f4
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-read-data-from-the-windows-registry-ccli"></a>如何：從 Windows 登錄讀取資料 (C++/CLI)
下列程式碼範例使用<xref:Microsoft.Win32.Registry.CurrentUser>從 Windows 登錄讀取資料的索引鍵。 首先，使用列舉子機碼<xref:Microsoft.Win32.RegistryKey.GetSubKeyNames%2A>方法，然後識別子機碼使用開啟<xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A>方法。 根目錄機碼，例如每個子機碼由<xref:Microsoft.Win32.RegistryKey>類別。 最後，新<xref:Microsoft.Win32.RegistryKey>物件用來列舉的索引鍵/值組。  
  
## <a name="example"></a>範例  
  
### <a name="code"></a>程式碼  
  
```  
// registry_read.cpp  
// compile with: /clr  
using namespace System;  
using namespace Microsoft::Win32;  
  
int main( )  
{  
   array<String^>^ key = Registry::CurrentUser->GetSubKeyNames( );  
  
   Console::WriteLine("Subkeys within CurrentUser root key:");  
   for (int i=0; i<key->Length; i++)  
   {  
      Console::WriteLine("   {0}", key[i]);  
   }  
  
   Console::WriteLine("Opening subkey 'Identities'...");  
   RegistryKey^ rk = nullptr;  
   rk = Registry::CurrentUser->OpenSubKey("Identities");  
   if (rk==nullptr)  
   {  
      Console::WriteLine("Registry key not found - aborting");  
      return -1;  
   }  
  
   Console::WriteLine("Key/value pairs within 'Identities' key:");  
   array<String^>^ name = rk->GetValueNames( );  
   for (int i=0; i<name->Length; i++)  
   {  
      String^ value = rk->GetValue(name[i])->ToString();  
      Console::WriteLine("   {0} = {1}", name[i], value);  
   }  
  
   return 0;  
}  
```  
  
## <a name="remarks"></a>備註  
 <xref:Microsoft.Win32.Registry>類別是只是靜態的執行個體的容器<xref:Microsoft.Win32.RegistryKey>。 每個執行個體表示登錄根節點。 執行個體<xref:Microsoft.Win32.Registry.ClassesRoot>， <xref:Microsoft.Win32.Registry.CurrentConfig>， <xref:Microsoft.Win32.Registry.CurrentUser>， <xref:Microsoft.Win32.Registry.LocalMachine>，和<xref:Microsoft.Win32.Registry.Users>。  
  
 此外為靜態中的物件<xref:Microsoft.Win32.Registry>類別是唯讀狀態。 此外，執行個體的<xref:Microsoft.Win32.RegistryKey>類別會建立用來存取登錄的內容物件以及處於唯讀狀態。 如需如何覆寫這個行為的範例，請參閱[How to： 將資料寫入至 Windows 登錄 (C + + /CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)。  
  
 有兩個額外的物件中<xref:Microsoft.Win32.Registry>類別：<xref:Microsoft.Win32.Registry.DynData>和<xref:Microsoft.Win32.Registry.PerformanceData>。 執行個體都<xref:Microsoft.Win32.RegistryKey>類別。 <xref:Microsoft.Win32.Registry.DynData>物件包含動態登錄資訊，僅適用於在 Windows 98 和 Windows me。 <xref:Microsoft.Win32.Registry.PerformanceData>物件可以用來存取應用程式使用 Windows 效能監視系統的效能計數器資訊。 <xref:Microsoft.Win32.Registry.PerformanceData>節點表示資訊不會實際儲存在登錄中，因此無法檢視使用 Regedit.exe。  
  
## <a name="see-also"></a>請參閱  
 [如何： 將資料寫入至 Windows 登錄 (C + + /CLI)](../dotnet/how-to-write-data-to-the-windows-registry-cpp-cli.md)   
 [Windows 作業 (C + + /CLI)](../dotnet/windows-operations-cpp-cli.md)   
 [以 C++/CLI 進行 .NET 程式設計 (Visual C++)](../dotnet/dotnet-programming-with-cpp-cli-visual-cpp.md)