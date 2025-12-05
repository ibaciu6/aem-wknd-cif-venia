# AEM WKND + CIF Venia Merged Project

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Java 21](https://img.shields.io/badge/Java-21-blue.svg)](https://openjdk.org/projects/jdk/21/)
[![Maven 3.9.4+](https://img.shields.io/badge/Maven-3.9.4+-green.svg)](https://maven.apache.org/)

A merged Adobe Experience Manager (AEM) project combining two official Adobe reference implementations:

- **[WKND Sites](https://github.com/adobe/aem-guides-wknd)** - Adobe's full-stack Sites reference implementation for a lifestyle brand
- **[Venia Commerce](https://github.com/adobe/aem-cif-guides-venia)** - Adobe's Commerce Integration Framework (CIF) reference storefront

This project demonstrates how to integrate content management and commerce capabilities in a single AEM installation, creating a unified demo environment with both a content-driven website (WKND) and a commerce-enabled storefront (Venia).

![WKND Screenshot](https://user-images.githubusercontent.com/8974514/119887685-489f7800-bee9-11eb-9db1-95c641e7c4ea.jpg)

## 🎯 Use Cases

- **Learning & Training**: Explore both WKND content management and Venia commerce patterns in one environment
- **Demo Environment**: Showcase AEM's full capabilities including Sites + Commerce
- **Development Reference**: Starting point for projects requiring both content and commerce functionality
- **POC/Prototyping**: Quick setup for proof-of-concept implementations

## 📦 What's Included

### WKND Sites
- Complete multi-language reference site (US, CA, DE, ES, FR)
- Core Components integration
- Experience Fragments (header, footer)
- Content Fragments
- Responsive design with modern frontend

### Venia Commerce (CIF)
- Product catalog structure
- Product detail pages
- Cart and checkout flow
- Account management pages
- Commerce-specific components
- GraphQL/Magento integration ready

## 🔧 Prerequisites

| Requirement | Version |
|------------|---------|
| Java | 21 |
| Maven | 3.9.4+ |
| AEM SDK | Cloud Service or 6.5 LTS |
| Node.js | 16+ (for frontend build) |

## 🚀 Quick Start

### Clone the Repository

```bash
git clone https://github.com/ibaciu6/aem-wknd-cif-venia.git
cd aem-wknd-cif-venia
```

### Build the Project

**For AEM as a Cloud Service SDK:**

```bash
mvn clean install -PautoInstallSinglePackage
```

**For AEM 6.5:**

```bash
mvn clean install -PautoInstallSinglePackage -Pclassic
```

### Build Without Installing

```bash
mvn clean install
```

The main package will be generated at: `all/target/aem-wknd-cif-venia.all-1.0.0-SNAPSHOT.zip`

## 📁 Project Structure

```
aem-wknd-cif-venia/
├── all/                    # Container package (deploy this)
├── core/                   # Java bundle (WKND + Venia models)
│   ├── com.adobe.aem.guides.wknd.*
│   └── venia.core.*
├── ui.apps/               # Components and templates
│   ├── /apps/wknd         # WKND components
│   └── /apps/venia        # Venia commerce components
├── ui.apps.structure/     # Repository structure
├── ui.config/             # OSGi configurations
├── ui.content/            # Content structure
│   ├── /content/wknd      # WKND pages
│   ├── /content/venia     # Venia pages
│   ├── /conf/wknd         # WKND templates
│   └── /conf/venia        # Venia templates
├── ui.content.sample/     # Sample content
├── ui.frontend/           # Frontend build (webpack)
├── dispatcher/            # Dispatcher configuration
├── it.tests/              # Integration tests
└── ui.tests/              # UI tests (Cypress)
```

## 🌐 Accessing the Sites

After deployment, access the sites at:

### Author Instance (localhost:4502)

| Site | URL |
|------|-----|
| WKND Homepage | http://localhost:4502/content/wknd/us/en.html |
| WKND Editor | http://localhost:4502/editor.html/content/wknd/us/en.html |
| Venia Homepage | http://localhost:4502/content/venia/us/en.html |
| Venia Editor | http://localhost:4502/editor.html/content/venia/us/en.html |
| Sites Console | http://localhost:4502/sites.html/content |

### Publish Instance (localhost:4503)

| Site | URL |
|------|-----|
| WKND | http://localhost:4503/content/wknd/us/en.html |
| Venia | http://localhost:4503/content/venia/us/en.html |

## ⚠️ Known Limitations

### CIF/Commerce Dependencies

The Venia commerce functionality requires:

1. **CIF Add-on**: Must be installed/enabled on your AEM environment
2. **Commerce Backend**: Magento/Adobe Commerce GraphQL endpoint for full functionality

Without these, the Venia commerce features will have limited functionality (pages render but product data won't load).

**WKND Sites functionality works independently and does not require any commerce backend.**

### Build Validation

Some content validators are configured with relaxed settings for the merged content:
- Replication metadata validation is relaxed
- UUID validation allows for merged content scenarios

This is intentional and safe for demo/development environments.

## 🧪 Running Tests

### Unit Tests

```bash
mvn clean test
```

### Integration Tests

```bash
mvn clean verify -PintegrationTests
```

### UI Tests (Cypress)

```bash
cd ui.tests/test-module
npm install
npm run test
```

## 📊 Build Results

| Component | Status |
|-----------|--------|
| Core Bundle | ✅ Builds successfully |
| UI Apps | ✅ Builds successfully |
| UI Content | ✅ Builds successfully |
| UI Frontend | ✅ Builds successfully |
| Dispatcher | ✅ Builds successfully |
| Unit Tests | ⚠️ Some CIF tests require mocking |

## 🤝 Contributing

Contributions are welcome! Please feel free to submit issues and pull requests.

1. Fork the repository
2. Create your feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📚 Related Resources

### WKND
- [WKND Tutorial](https://experienceleague.adobe.com/docs/experience-manager-learn/getting-started-wknd-tutorial-develop/overview.html)
- [WKND GitHub Repository](https://github.com/adobe/aem-guides-wknd)
- [Live Demo](https://www.wknd.site/)

### Venia/CIF
- [CIF Documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service/content/content-and-commerce/home.html)
- [Venia GitHub Repository](https://github.com/adobe/aem-cif-guides-venia)
- [CIF Core Components](https://github.com/adobe/aem-core-cif-components)

### AEM
- [AEM Core Components](https://github.com/adobe/aem-core-wcm-components)
- [AEM Project Archetype](https://github.com/adobe/aem-project-archetype)
- [AEM as a Cloud Service Documentation](https://experienceleague.adobe.com/docs/experience-manager-cloud-service.html)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ⚖️ Attribution

This project is a merge of two Adobe open-source projects:
- [adobe/aem-guides-wknd](https://github.com/adobe/aem-guides-wknd) - MIT License
- [adobe/aem-cif-guides-venia](https://github.com/adobe/aem-cif-guides-venia) - Apache 2.0 License

Many images in the WKND reference site are from Adobe Stock. See Adobe's [terms](https://www.adobe.com/legal/terms.html) for usage restrictions.

---

**Disclaimer**: This is a community project for learning and demonstration purposes. It is not officially supported by Adobe.
