<script lang="ts">
  import Drawer, {
    AppContent,
    Content,
    Header,
    Subtitle,
    Scrim,
  } from "@smui/drawer";
  import Button, { Label } from "@smui/button";
  import List, { Item, Text, Graphic, Separator, Subheader } from "@smui/list";
  import TopAppBar, {
    Row,
    Section,
    Title,
    AutoAdjust,
  } from "@smui/top-app-bar";
  import IconButton, { Icon } from "@smui/icon-button";

  let open = false;
  let active = "Inbox";

  function setActive(value: string) {
    active = value;
    open = false;
  }

  let topAppBar: TopAppBar;
</script>

<TopAppBar bind:this={topAppBar} variant="fixed">
  <Row>
    <Section>
      <IconButton class="material-icons" on:click={() => (open = !open)}
        >menu</IconButton
      >
      <Title>Static</Title>
    </Section>
    <Section align="end" toolbar>
      <IconButton class="material-icons" aria-label="Download"
        >file_download</IconButton
      >
      <IconButton class="material-icons" aria-label="Print this page"
        >print</IconButton
      >
      <IconButton class="material-icons" aria-label="Bookmark this page"
        >bookmark</IconButton
      >
    </Section>
  </Row>
</TopAppBar>

<Drawer variant="modal" bind:open>
  <Header>
    <Title>App Title</Title>
    <Subtitle>App Subtitle</Subtitle>
  </Header>
  <Content>
    <List>
      <Item
        href="javascript:void(0)"
        on:click={() => setActive("Inbox")}
        activated={active === "Inbox"}
      >
        <Graphic class="material-icons" aria-hidden="true">inbox</Graphic>
        <Text>Inbox</Text>
      </Item>
      <Item
        href="javascript:void(0)"
        on:click={() => setActive("Star")}
        activated={active === "Star"}
      >
        <Graphic class="material-icons" aria-hidden="true">star</Graphic>
        <Text>Star</Text>
      </Item>
      <Item
        href="javascript:void(0)"
        on:click={() => setActive("Sent Mail")}
        activated={active === "Sent Mail"}
      >
        <Graphic class="material-icons" aria-hidden="true">send</Graphic>
        <Text>Sent Mail</Text>
      </Item>
      <Item
        href="javascript:void(0)"
        on:click={() => setActive("Drafts")}
        activated={active === "Drafts"}
      >
        <Graphic class="material-icons" aria-hidden="true">drafts</Graphic>
        <Text>Drafts</Text>
      </Item>

      <Separator />
      <Subheader tag="h6">Labels</Subheader>
      <Item
        href="javascript:void(0)"
        on:click={() => setActive("Family")}
        activated={active === "Family"}
      >
        <Graphic class="material-icons" aria-hidden="true">bookmark</Graphic>
        <Text>Family</Text>
      </Item>
      <Item
        href="javascript:void(0)"
        on:click={() => setActive("Friends")}
        activated={active === "Friends"}
      >
        <Graphic class="material-icons" aria-hidden="true">bookmark</Graphic>
        <Text>Friends</Text>
      </Item>
      <Item
        href="javascript:void(0)"
        on:click={() => setActive("Work")}
        activated={active === "Work"}
      >
        <Graphic class="material-icons" aria-hidden="true">bookmark</Graphic>
        <Text>Work</Text>
      </Item>
    </List>
  </Content>
</Drawer>

<Scrim />
<AppContent>
  <AutoAdjust {topAppBar}>
    <pre class="status">Active: {active}</pre>
    <slot />
  </AutoAdjust>
</AppContent>

<style>
  :global(body) {
    margin: 0;
    padding: 0;
  }
</style>
