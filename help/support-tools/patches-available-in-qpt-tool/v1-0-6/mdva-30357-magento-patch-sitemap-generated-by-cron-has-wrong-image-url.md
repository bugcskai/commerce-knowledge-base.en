---
title: 'MDVA-30357: sitemap generated by cron has wrong image URL'
description: The MDVA-30357 patch fixes the issue with the wrong image URL being created by a cron generated sitemap in the Commerce Admin. This patch is available when the [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is installed. Please note that the issue was fixed in Adobe Commerce 2.4.2.
exl-id: c91f7ae0-0970-4918-9d1f-4ede6bfcb05f
---
# MDVA-30357: sitemap generated by cron has wrong image URL

The MDVA-30357 patch fixes the issue with the wrong image URL being created by a cron generated sitemap in the Commerce Admin. This patch is available when the [Quality Patches Tool (QPT)](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) 1.0.6 is installed. Please note that the issue was fixed in Adobe Commerce 2.4.2.

## Affected products and versions

* Adobe Commerce (all deployment methods) 2.3.2 to 2.4.0

>[!NOTE]
>
>The patch might become applicable to other versions with new Quality Patches Tool releases. To check if the patch is compatible with your Adobe Commerce version, update the `magento/quality-patches` package to the latest version and check the compatibility on the [QPT landing page](https://devdocs.magento.com/quality-patches/tool.html#patch-grid). Use the patch ID as a search keyword to locate the patch.

## Issue

Sitemaps generated by cron in Adobe Commerce contain the wrong image URL path.

<u>Steps to reproduce</u>:

1. In the Commerce Admin, create a new website, store, or store view.
1. Add at least one product to each store, and add at least one image to each product.
1. Enable **Sitemap Generation By Schedule** in **Admin** > **Stores** > **Configuration** > **CATALOG** > **XML Sitemap** > **Generation Settings**.
1. Generate a sitemap for any of the two stores manually in **Admin** > **Marketing** > **Site Map** using a sitemap name like "*sitemap.xml*".
    * Rename the file to something like "*manual\_sitemap.xml*" or copy the file content to any text editor.
1. Generate the same sitemap by cron job `sitemap_generate`.
1. Compare the manually generated sitemap "*manual\_sitemap.xml*" and the sitemap generated by cron "*sitemap.xml*".

<u>Expected results</u>:

The cached sitemap image path URL is correct.

<u>Actual results</u>:

The sitemap generated by cron contains the wrong image path URL. If you try to open the image from "*sitemap.xml*", it will show a default placeholder. Manually generated sitemap URLs are unaffected by this issue.

## Apply the patch

To apply individual patches, use the following links depending on your deployment method:

* Adobe Commerce or Magento Open Source on-premises: [Software Update Guide > Apply Patches](https://devdocs.magento.com/guides/v2.4/comp-mgr/patching/mqp.html) in our developer documentation.
* Adobe Commerce on cloud infrastructure: [Upgrades and Patches > Apply Patches](https://devdocs.magento.com/cloud/project/project-patch.html) in our developer documentation.

## Related reading

To learn more about Quality Patches Tool, refer to:

* [Quality Patches Tool released: a new tool to self-serve quality patches](/help/announcements/adobe-commerce-announcements/magento-quality-patches-released-new-tool-to-self-serve-quality-patches.md) in our support knowledge base.
* [Check if patch is available for your Adobe Commerce issue using Quality Patches Tool](/help/support-tools/patches-available-in-qpt-tool/check-patch-for-magento-issue-with-magento-quality-patches.md) in our support knowledge base.

For info about other patches available in QPT, refer to [Patches available in QPT](https://devdocs.magento.com/quality-patches/tool.html#patch-grid) in our developer documentation.

To learn more about sitemaps, refer to these articles in our developer documentation:

* [Add sitemap and search engine robots](https://devdocs.magento.com/cloud/trouble/robots-sitemap.html)
* [Configure and run cron](https://devdocs.magento.com/guides/v2.4/config-guide/cli/config-cli-subcommands-cron.html)
* [Secure cron.php to run in a browser](https://devdocs.magento.com/guides/v2.4/config-guide/secy/secy-cron.html)