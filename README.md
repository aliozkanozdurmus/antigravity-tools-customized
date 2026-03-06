# Antigravity Tools Customized

> Antigravity Tools tabanlı, Türkçe dokümantasyonlu ve sadeleştirilmiş kişisel fork.

Bu repo; çoklu AI hesabı yönetimi, API proxy ve model yönlendirme ihtiyaçları için kullanılan masaüstü uygulamanın özelleştirilmiş sürümüdür.

## Özellikler

- Çoklu hesap yönetimi (Google/Anthropic tabanlı akışlar)
- OpenAI uyumlu endpoint desteği (`/v1/chat/completions`)
- Anthropic uyumlu endpoint desteği (`/v1/messages`)
- Gemini uyumlu entegrasyon akışı
- Model yönlendirme ve hesap rotasyonu
- Tauri + React tabanlı masaüstü arayüz

## Hızlı Kurulum

### Seçenek 1: Kurulum Scripti

Linux/macOS:

```bash
curl -fsSL https://raw.githubusercontent.com/lbjlaq/Antigravity-Manager/main/install.sh | bash
```

Windows PowerShell:

```powershell
irm https://raw.githubusercontent.com/lbjlaq/Antigravity-Manager/main/install.ps1 | iex
```

### Seçenek 2: Kaynak Koddan Geliştirme

```bash
npm install
npm run dev
```

Tauri masaüstü geliştirme modu:

```bash
npm run tauri dev
```

## Docker ile Çalıştırma (Opsiyonel)

```bash
docker run -d --name antigravity-manager \
  -p 8045:8045 \
  -e API_KEY=sk-your-api-key \
  -e WEB_PASSWORD=your-login-password \
  -v ~/.antigravity_tools:/root/.antigravity_tools \
  lbjlaq/antigravity-manager:latest
```

## Temel Kullanım

Uygulamada proxy servisini başlattıktan sonra yerel adresi istemcilerine ver.

- API Base URL: `http://127.0.0.1:8045`
- OpenAI tarzı istemciler için: `http://127.0.0.1:8045/v1`

Claude CLI örneği:

```bash
export ANTHROPIC_API_KEY="sk-antigravity"
export ANTHROPIC_BASE_URL="http://127.0.0.1:8045"
claude
```

## Dizin Yapısı (Özet)

- `src/`: React arayüz kodu
- `src-tauri/`: Rust/Tauri masaüstü katmanı
- `docker/`: container kurulum dosyaları
- `docs/`: ekran görüntüleri ve dokümanlar

## Güvenlik Notu

- Gerçek API anahtarlarını repoya commit etme.
- `API_KEY`, `WEB_PASSWORD` gibi değerleri sadece yerel/.env veya secret manager üzerinden kullan.

## Kaynak ve Teşekkür

Bu çalışma, aşağıdaki üst projeyi temel alır:

- Upstream: `lbjlaq/Antigravity-Manager`

Lisans ve telif detayları için `LICENSE` dosyasını incele.
