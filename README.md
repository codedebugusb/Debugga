import { ApifyClient } from 'apify-client';

// Initialize the ApifyClient with API token
const client = new ApifyClient({
    token: '<YOUR_API_TOKEN>',
});

(async () => {
    // Run the Actor task and wait for it to finish
    const run = await client.task("lrTcbPEXNc7rBroDI").call();

    // Fetch and print Actor task results from the run's dataset (if any)
    console.log('Results from dataset');
    const { items } = await client.dataset(run.defaultDatasetId).listItems();
    items.forEach((item) => {
        console.dir(item);
    });
})();

## INPUT_SCHEMA.json
```json
{
    "title": "Investigator Actor Input",
    "type": "object",
    "schemaVersion": 1,
    "properties": {
        "startUrls": {
            "title": "Start URLs",
            "type": "array",
            "description": "URLs to investigate",
            "editor": "requestListSources",
            "default": ["https://example.com"]
        },
        "searchTerms": {
            "title": "Search Terms",
            "type": "array",
            "description": "Specific terms to search for",
            "editor": "stringList",
            "default": []
        },
        "investigationType": {
            "title": "Investigation Type",
            "type": "string",
            "description": "Type of investigation to perform",
            "enum": ["general", "company", "person", "news"],
            "default": "general"
        },
        "maxRequestsPerCrawl": {
            "title": "Max Requests",
            "type": "integer",
            "description": "Maximum number of pages to crawl",
            "default": 10,
            "minimum": 1
        },
        "extractEmails": {
            "title": "Extract Emails",
            "type": "boolean",
            "description": "Extract email addresses",
            "default": true
        },
        "extractPhones": {
            "title": "Extract Phone Numbers",
            "type": "boolean",
            "description": "Extract phone numbers",
            "default": true
        },
        "extractSocialLinks": {
            "title": "Extract Social Media Links",
            "type": "boolean",
            "description": "Extract social media links",
            "default": true
        },
        "deepScan": {
            "title": "Deep Scan",
            "type": "boolean",
            "description": "Follow links to related pages",
            "default": false
        }
    },
    "required": ["startUrls"]
}
```
import { ApifyClient } from 'apify-client';

// Initialize the ApifyClient with API token
const client = new ApifyClient({
    token: '<YOUR_API_TOKEN>',
});

// Prepare Actor input
const input = {
    "helloWorld": 123
};

(async () => {
    // Run the Actor and wait for it to finish
    const run = await client.actor("nCoCzy8GS06IBvoS0").call(input);

    // Fetch and print Actor results from the run's dataset (if any)
    console.log('Results from dataset');
    const { items } = await client.dataset(run.defaultDatasetId).listItems();
    items.forEach((item) => {
        console.dir(item);
    });
})();

