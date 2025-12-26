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
