<script>
    import ScrollIntoViewAnchor from "$lib/components/buttons/ScrollIntoViewAnchor.svelte";
import { Argument, ReturnType, Docs } from "$lib/components/syntax";
    import { scrollIntoView } from "$lib/functions";

    const exampleCode = `import { KinshipContext } from "@Kinship/Kinship";
// initialize connection with desired adapter as \`connection\`.
const ctx: KinshipContext<Track> = new KinshipContext(connection, "Track"));
ctx.hasOne(m => m.PlaylistTrack.withKeys("TrackId", "TrackId"))`;

    const sqlCode = `SELECT * ...`
</script>

<h2 class="h2">.hasOne()</h2>
<div class="p-4">
    Configure a one-to-one relationship on your <code class="code">KinshipContext</code> class object to be included in future queries.
    <Docs {exampleCode}>
        <svelte:fragment slot="note">
            This call will only send a command to your database asking for information about the table. (or otherwise, <code class="code">DESCRIBE</code> the table)
            <br>
            To include the table as a <code class="code">JOIN</code> statement, then you need to use <ScrollIntoViewAnchor isCode href="#include" label=".include()"/>.
        </svelte:fragment>
        <svelte:fragment slot="parameters">
            <Argument name="modelCallback" type="ConfigurationCallback">
                Callback that uses the <code class="code">model</code> parameter to get reference to the property being configured.
            </Argument>
        </svelte:fragment>
        <svelte:fragment slot="returns">
            <ReturnType type="KinshipContext">
                Same reference to the <code class="code">KinshipContext</code> class object.
            </ReturnType>
        </svelte:fragment>
    </Docs>
</div>