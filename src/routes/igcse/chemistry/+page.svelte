<script lang="ts">
  import DataTable, { Head, Body, Row, Cell } from '@smui/data-table'
  import LinkTree from '$lib/components/LinkTree.svelte'

  export let data

  let rows: [string, boolean, boolean, boolean][] = [
    ['Experimental Techniques', true, true, true],
    ['Stoichiometry', true, true, true],
    ['Reactions', true, true, true],
    ['Electrolysis', true, true, true],
    ['Periodic Table', true, true, true],
    ['Metals', true, true, true],
    ['Organic Chemistry', true, true, true]
  ]

  let page = 'IGCSE Chemistry'
</script>

<svelte:head>
  <title>{page}</title>
  <meta property="og:title" content={page} />
  <meta
    property="og:description"
    content={`Read ${page} notes and answer topic questions for free!`}
  />
</svelte:head>

<section>
  <h1>Chemistry</h1>
  <h2>Syllabus</h2>
  <p>
    The double and combined column refer to <a
      href="https://www.cambridgeinternational.org/Images/597069-2023-2024-syllabus.pdf"
      target="_blank">co-ordinated sciences</a
    >
    and
    <a
      href="https://www.cambridgeinternational.org/images/557017-2022-syllabus-.pdf"
      target="_blank">combined sciences</a
    > respectively.
  </p>
  <DataTable>
    <Head>
      <Row>
        <Cell>Topic</Cell>
        <Cell>Separate</Cell>
        <Cell>Double</Cell>
        <Cell>Combined</Cell>
      </Row>
    </Head>
    <Body>
      {#each rows as row}
        <Row>
          {#each row as cell, i}
            <Cell>
              {#if i === 0 && typeof cell === 'string'}
                <a href={[data.pathname, cell.replaceAll(' ', '_').toLowerCase()].join('/')}
                  >{cell}</a
                >
              {:else}
                <span class="material-symbols-rounded" style="text-align: center; width: 100%;"
                  >{cell ? 'check' : 'close'}</span
                >
              {/if}
            </Cell>
          {/each}
        </Row>
      {/each}
    </Body>
  </DataTable>
  <h2>Practical</h2>
  <p>
    The <strong>alternative to practical</strong> paper assesses practical skills and includes writing
    about experiments.
  </p>
  <h3>Apparatus</h3>
  <ul>
    <li>Test Tube</li>
    <li>Conical Flask</li>
    <li>Beaker</li>
    <li>Gas Syringe</li>
    <li>Measuring Cylinder</li>
    <li>Volumetric Pipette</li>
    <li>Dropping/teat Pipette</li>
    <li>Burette</li>
    <li>Glass Rod</li>
    <li>Delivery Tube</li>
  </ul>
  <LinkTree url={data.pathname} glob={import.meta.glob('./**/+page.svelte')}></LinkTree>
</section>
