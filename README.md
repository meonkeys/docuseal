<h1 align="center" style="border-bottom: none">
  <div>
    A <a href="https://www.docuseal.com">DocuSeal</a> Fork
  </div>
</h1>
<h3 align="center">
This is a DocuSeal fork intended for security and privacy upgrades. Consider upstream DocuSeal first.
</h3>

See:

* [upstream DocuSeal code](https://github.com/docusealco/docuseal)
* [Reddit r/selfhosted post: Phone home tracking image in DocuSeal, and how to remove it](https://www.reddit.com/r/selfhosted/comments/1dr2nby/phone_home_tracking_image_in_docuseal_and_how_to/)
* [same, crossposted to Lemmy.World](https://lemmy.world/post/17046423)

There are a couple ways to show how this differs from [upstream](https://github.com/docusealco/docuseal). Locally: first clone this repository, then add the upstream repository as an additional remote. Assuming they are called `origin` and `upstream` respectively, run `git log -p --stat origin/master..master`. At the time of writing I have added only two significant commits: `remove github stars badge` and `remove link in email footer`, with a total of 1 changed and 3 deleted lines of code. You can also visualize changes from upstream by clicking [x commits ahead of](https://github.com/meonkeys/docuseal/compare/docusealco%3Adocuseal%3Amaster...master) on my fork's home page at GitHub.

My convention for releases is to create an `a` tag building on top of an official release. For example, [1.6.4](https://github.com/docusealco/docuseal/releases/tag/1.6.4) is theirs, and [1.6.4a](https://github.com/meonkeys/docuseal/releases/tag/1.6.4a) is their 1.6.4 release plus my changes.

I'll keep an eye upstream and upgrade periodically, but I really hope this isn't a long-lived fork. 

It might not be too much work to keep it going (it's such a tiny fork) but I want to be realistic. I'm not committing to support this like they are.

If you decide to use this and I miss an important change upstream (especially a security update), feel free to create a PR and I'll take a look. Probably the best approach would be for us all to thumbs-up https://github.com/docusealco/docuseal/issues/302 . They should understand that users don't want mandatory tracking (and if it somehow isn't acutally tracking, I guess they can clarify).

Related: I'd love to come up with a generic solution for controlling outbound traffic from containers. Looks like most people use iptables to do this? I see there's a DOCKER_USER chain built for customizations. I need to finally figure out iptables or find an easier way to do this.

https://docs.docker.com/network/packet-filtering-firewalls/

https://serverfault.com/questions/704643/steps-for-limiting-outside-connections-to-docker-container-with-iptables

<p align="center">
  <a href="https://hub.docker.com/r/docuseal/docuseal">
    <img alt="Docker releases" src="https://img.shields.io/docker/v/docuseal/docuseal">
  </a>
  <a href="https://discord.gg/qygYCDGck9">
    <img src="https://img.shields.io/discord/1125112641170448454?logo=discord"/>
  </a>
  <a href="https://twitter.com/intent/follow?screen_name=docusealco">
    <img src="https://img.shields.io/twitter/follow/docusealco?style=social" alt="Follow @docusealco" />
  </a>
</p>
<p>
DocuSeal is an open source platform that provides secure and efficient digital document signing and processing. Create PDF forms to have them filled and signed online on any device with an easy-to-use, mobile-optimized web tool.
</p>
<h2 align="center">
  <a href="https://demo.docuseal.tech">✨ Live Demo</a>
  <span>|</span>
  <a href="https://docuseal.com/sign_up">☁️ Try in Cloud</a>
</h2>

## Features
- PDF form fields builder (WYSIWYG)
- 12 field types available (Signature, Date, File, Checkbox etc.)
- Multiple submitters per document
- Automated emails via SMTP
- Files storage on disk or AWS S3, Google Storage, Azure Cloud
- Automatic PDF eSignature
- PDF signature verification
- Users management
- Mobile-optimized
- 6 UI languages with signing available in 13 languages
- API and Webhooks for integrations
- Easy to deploy in minutes

## Pro Features
- Company logo and white-label
- User roles
- Automated reminders
- Invitation and identify verification via SMS
- Conditional fields and formulas
- Bulk send with CSV, XLSX spreadsheet import
- SSO / SAML
- Template creation with HTML API ([Guide](https://www.docuseal.com/guides/create-pdf-document-fillable-form-with-html-api))
- Template creation with PDF or DOCX and field tags API ([Guide](https://www.docuseal.com/guides/use-embedded-text-field-tags-in-the-pdf-to-create-a-fillable-form))
- Embedded signing form ([React](https://github.com/docusealco/docuseal-react), [Vue](https://github.com/docusealco/docuseal-vue), [Angular](https://github.com/docusealco/docuseal-angular) or [JavaScript](https://www.docuseal.com/docs/embedded))
- Embedded document form builder ([React](https://github.com/docusealco/docuseal-react), [Vue](https://github.com/docusealco/docuseal-vue), [Angular](https://github.com/docusealco/docuseal-angular) or [JavaScript](https://www.docuseal.com/docs/embedded))
- [Learn more](https://www.docuseal.com/pricing)

## Deploy

|Heroku|Railway|
|:--:|:---:|
| [<img alt="Deploy on Heroku" src="https://www.herokucdn.com/deploy/button.svg" height="40">](https://heroku.com/deploy?template=https://github.com/docusealco/docuseal-heroku) | [<img alt="Deploy on Railway" src="https://railway.app/button.svg" height="40">](https://railway.app/template/IGoDnc?referralCode=ruU7JR)|
|**DigitalOcean**|**Render**|
| [<img alt="Deploy on DigitalOcean" src="https://www.deploytodo.com/do-btn-blue.svg" height="40">](https://cloud.digitalocean.com/apps/new?repo=https://github.com/docusealco/docuseal-digitalocean/tree/master&refcode=421d50f53990) | [<img alt="Deploy to Render" src="https://render.com/images/deploy-to-render-button.svg" height="40">](https://render.com/deploy?repo=https://github.com/docusealco/docuseal-render)

#### Docker

```sh
docker run --name docuseal -p 3000:3000 -v.:/data docuseal/docuseal
```

By default DocuSeal docker container uses an SQLite database to store data and configurations. Alternatively, it is possible use PostgreSQL or MySQL databases by specifying the `DATABASE_URL` env variable.

#### Docker Compose

Download docker-compose.yml into your private server:
```sh
curl https://raw.githubusercontent.com/docusealco/docuseal/master/docker-compose.yml > docker-compose.yml
```

Run the app under a custom domain over https using docker compose (make sure your DNS points to the server to automatically issue ssl certs with Caddy):
```sh
sudo HOST=your-domain-name.com docker compose up
```

## For Businesses
### Integrate seamless document signing into your web or mobile apps with DocuSeal

At DocuSeal we have expertise and technologies to make documents creation, filling, signing and processing seamlessly integrated with your product. We specialize in working with various industries, including **Banking, Healthcare, Transport, Real Estate, eCommerce, KYC, CRM, and other software products** that require bulk document signing. By leveraging DocuSeal, we can assist in reducing the overall cost of developing and processing electronic documents while ensuring security and compliance with local electronic document laws.

[Book a Meeting](https://www.docuseal.com/contact)

## License

Distributed under the AGPLv3 License. See [LICENSE](https://github.com/docusealco/docuseal/blob/master/LICENSE) for more information.
Unless otherwise noted, all files © 2023 DocuSeal LLC.

## Tools

- [Signature Maker](https://www.docuseal.com/online-signature)
- [Sign Document Online](https://www.docuseal.com/sign-documents-online)
- [Fill PDF Online](https://www.docuseal.com/fill-pdf)
