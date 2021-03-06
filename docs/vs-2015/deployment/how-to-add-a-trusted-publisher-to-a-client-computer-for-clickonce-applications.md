---
title: '方法: ClickOnce アプリケーション用の信頼された発行者をクライアントコンピューターに追加する |Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, install without prompting
- trusted application deployment, Trusted Publishers
ms.assetid: 35fe324c-45a1-4509-b7be-5c18b4b1b4ab
caps.latest.revision: 12
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 296aec3b2b5cd307400b230375a7171f158fee60
ms.sourcegitcommit: c150d0be93b6f7ccbe9625b41a437541502560f5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/10/2020
ms.locfileid: "75847694"
---
# <a name="how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications"></a>方法: ClickOnce アプリケーション用の信頼された発行者をクライアント コンピューターに追加する
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

信頼されたアプリケーションの配置を使用すると、 [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションをユーザーに確認することなく高いレベルの信頼で実行できるように、クライアント コンピューターを構成できます。 以下の手順では、コマンド ライン ツールの CertMgr.exe を使用して、クライアント コンピューターの信頼された発行者ストアに発行者の証明書を追加する方法について説明します。  
  
 使用するコマンドは、証明書を発行した証明機関 (CA) が、クライアント コンピューターの信頼されたルートに属しているかどうかによって多少異なります。 Windows クライアント コンピューターがドメインに属している場合、コンピューターは、信頼されたルートと見なす CA を一覧として保持しています。 この一覧は通常、システム管理者が設定します。 証明書が、これらの信頼されたルートのいずれかから発行されたものであるか、これらの信頼されたルートのいずれかにつながっている CA によって発行された証明書である場合には、クライアント コンピューターの信頼されたルート証明書ストアにその証明書を追加できます。 一方、上記の信頼されたルートのいずれかによって発行された証明書でない場合には、クライアント コンピューターの信頼されたルート証明書ストアおよび信頼された発行者ストアの両方にその証明書を追加する必要があります。  
  
> [!NOTE]
> このようにして、昇格されたアクセス権を必要とする [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションを配置する予定のクライアント コンピューターすべてに対して、証明書を追加する必要があります。 証明書の追加は、手動で行うか、クライアント コンピューターに配置するアプリケーション経由で行います。 コンピューターの構成は一度だけ行う必要があります。一度構成すると、同じ証明書で署名された [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] アプリケーションは好きな数だけ配置できます。  
  
 証明書は、 <xref:System.Security.Cryptography.X509Certificates.X509Store> クラスを使用して、プログラムでストアに追加することもできます。  
  
 信頼されたアプリケーションの配置の概要については、「 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)」を参照してください。  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-the-trusted-root"></a>信頼されたルートの下の信頼された発行者ストアに証明書を追加するには  
  
1. CA からデジタル証明書を取得します。  
  
2. 証明書を Base64 X.509 (.cer) 形式でエクスポートします。 証明書の形式の詳細については、「 [証明書をエクスポートする](https://technet.microsoft.com/library/cc730988(WS.10).aspx)」を参照してください。  
  
3. クライアント コンピューターのコマンド プロンプトで、次のコマンドを実行します。  
  
     **certmgr.exe -add certificate.cer -c -s -r localMachine TrustedPublisher**  
  
### <a name="to-add-a-certificate-to-the-trusted-publishers-store-under-a-different-root"></a>他のルート下にある信頼された発行者ストアに証明書を追加するには  
  
1. CA からデジタル証明書を取得します。  
  
2. 証明書を Base64 X.509 (.cer) 形式でエクスポートします。 証明書の形式の詳細については、「 [証明書をエクスポートする](https://technet.microsoft.com/library/cc730988(WS.10).aspx)」を参照してください。  
  
3. クライアント コンピューターのコマンド プロンプトで、次のコマンドを実行します。  
  
     **certmgr.exe -add good.cer -c -s -r localMachine Root**  
  
     **certmgr.exe -add good.cer -c -s -r localMachine TrustedPublisher**  
  
## <a name="see-also"></a>参照  
 [チュートリアル : ClickOnce アプリケーションを手動で配置する](../deployment/walkthrough-manually-deploying-a-clickonce-application.md)   
 [ClickOnce アプリケーションのセキュリティ](../deployment/securing-clickonce-applications.md)   
 [ClickOnce アプリケーションのコード アクセス セキュリティ](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce と Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Trusted Application Deployment Overview](../deployment/trusted-application-deployment-overview.md)   
 [方法 : ClickOnce のセキュリティ設定を有効にする](../deployment/how-to-enable-clickonce-security-settings.md)   
 [方法 : ClickOnce アプリケーションのセキュリティ ゾーンを設定する](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [方法 : ClickOnce アプリケーションのカスタム アクセス許可を設定する](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [How to: Debug a ClickOnce Application with Restricted Permissions](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [方法: ClickOnce アプリケーション用の信頼された発行者をクライアント コンピューターに追加する](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [方法: アプリケーションマニフェストおよび配置マニフェストに再署名](../deployment/how-to-re-sign-application-and-deployment-manifests.md)する   
 [方法: ClickOnce 信頼プロンプトの動作を構成する](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)
