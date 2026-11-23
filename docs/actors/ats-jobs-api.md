---
title: "ATS Jobs API - 123 ATS: Greenhouse, Lever, Workday Jobs"
description: "ATS jobs API for 123 applicant tracking systems, each tested on a real employer: Greenhouse, Lever, Ashby, Workday and 119 more. Give a company domain, get every open job with salary, remote/hybrid/on-site, contract type, city, skills and apply link. $1.50 per 1,000 jobs, first 3 per run free."
---

[← All Actors](index.md) · [Catalogue home](../index.md)

# ATS Jobs API - 123 ATS: Greenhouse, Lever, Workday Jobs

ATS jobs API for 123 applicant tracking systems, each tested on a real employer: Greenhouse, Lever, Ashby, Workday and 119 more. Give a company domain, get every open job with salary, remote/hybrid/on-site, contract type, city, skills and apply link. $1.50 per 1,000 jobs, first 3 per run free.

**Run it on Apify:** [https://apify.com/om_kh/ats-jobs-api](https://apify.com/om_kh/ats-jobs-api) — browser, API, schedules, n8n / Make / Zapier, or an AI agent through MCP.

## In short

| | |
|---|---|
| **You give** | Company websites (`stripe.com`) or job board links, or tick **Search all companies** with a keyword and/or a city |
| **We do** | Find which hiring system runs the company's careers page (Greenhouse, Lever, Workday... 123 systems) and read its official public feed |
| **You get** | One row per open job: title, company, location, department, posted date, salary when published (with `has_salary` and a readable `salary_text` such as "USD 248,000-310,000 per year"), apply link, full description, plus facts read from the text (years of experience, skills, remote or office, visa) |
| **It costs** | $1.50 per 1,000 jobs (down to $0.90 on larger Apify plans), + $0.001 per run. A company with 35 open roles costs about **$0.05**. The first 3 jobs of every run are free; a run that finds nothing costs $0 |
| **It does not** | Scrape LinkedIn, Indeed or job boards, or read pages behind a login. Workday is capped at 200 roles per company |

## Input fields

| Field | Type | What it does |
|---|---|---|
| `companyDomains` | array | The easiest way to use this Actor. Default: `["stripe.com", "figma.com"]`. |
| `searchAllCompanies` | boolean | Search the open roles of thousands of companies at once, without giving any company: set at least one keyword or location below (e.g. keywords 'data engineer', locations 'Berlin'). Default: `false`. |
| `greenhouseBoards` | array | Company board tokens on Greenhouse (from boards.greenhouse.io/). |
| `leverCompanies` | array | Company handles on Lever (from jobs.lever.co/). |
| `ashbyBoards` | array | Board names on Ashby (from jobs.ashbyhq.com/). |
| `smartRecruitersCompanies` | array | Company identifiers on SmartRecruiters. |
| `ripplingCompanies` | array | Company handles on Rippling ATS (from ats.rippling.com/). |
| `breezyCompanies` | array | Company handles on Breezy HR (from .breezy.hr). |
| `workdayCareerUrls` | array | Full careers-site URLs on Workday, e.g. https://nvidia.wd5.myworkdayjobs.com/NVIDIAExternalCareerSite. |
| `personioCompanies` | array | Company handles on Personio (from .jobs.personio.de). |
| `bambooHrCompanies` | array | Company handles on BambooHR (from .bamboohr.com). |
| `recruiteeCompanies` | array | Recruitee: company from .recruitee.com. |
| `teamtailorCompanies` | array | Teamtailor: company from .teamtailor.com. |
| `workableAccounts` | array | Workable: account from apply.workable.com/. |
| `jobviteCompanies` | array | Jobvite: company from jobs.jobvite.com/. |
| `pinpointCompanies` | array | Pinpoint: company from .pinpointhq.com. |
| `gemCompanies` | array | Gem: company from jobs.gem.com/. |
| `joinCompanies` | array | JOIN: company from join.com/companies/. |
| `homerunCompanies` | array | Homerun: company from .homerun.co. |
| `hirehiveCompanies` | array | HireHive: company from .hirehive.com. |
| `manatalCompanies` | array | Manatal: company from careers-page.com/. |
| `doverCompanies` | array | Dover: company from app.dover.com/jobs/. |
| `avatureTenants` | array | Avature: tenant from .avature.net. |
| `pageupBoards` | array | PageUp: id/site from careers.pageuppeople.com//. |
| `zohoRecruitHosts` | array | Zoho Recruit: host like acme.zohorecruit.com. |
| `oracleCareerUrls` | array | Oracle Recruiting Cloud: full careers URL on oraclecloud.com (.../sites/). |
| `eightfoldCareerUrls` | array | Eightfold: careers URL, e.g. https://acme.eightfold.ai/careers. |
| `jazzHrCompanies` | array | JazzHR: company from .applytojob.com. |
| `comeetBoards` | array | Comeet: company/uid from comeet.com/jobs//, e.g. kaltura/E2.00D. |
| `icimsSites` | array | iCIMS: host like careers-acme.icims.com. |
| `trakstarCompanies` | array | Trakstar Hire: company from .hire.trakstar.com. |
| `ultiproBoardUrls` | array | UKG UltiPro: board URL on recruiting.ultipro.com (.../JobBoard/). |
| `paylocityBoards` | array | Paylocity: id or link from recruiting.paylocity.com/recruiting/jobs/All//.... |
| `applicantProSites` | array | ApplicantPro: site like acme.applicantpro.com. |
| `isolvedSites` | array | iSolved Hire: site like acme.isolvedhire.com. |
| `hireologyCompanies` | array | Hireology: company from careers.hireology.com/. |
| `hibobCompanies` | array | HiBob: company from .careers.hibob.com. |
| `hiringThingCompanies` | array | HiringThing: company from .hiringthing.com. |
| `cornerstoneSiteUrls` | array | Cornerstone: career site URL on csod.com (.../ux/ats/careersite//home?c=). |
| `freshteamCompanies` | array | Company from .freshteam.com. |
| `jobscoreCompanies` | array | Company code from careers.jobscore.com/careers/. |
| `successFactorsSites` | array | Career-site host, e.g. careers.ey.com. |
| `softgardenCompanies` | array | softgarden: company from .softgarden.io. |
| `factorialCompanies` | array | Factorial: company from .factorialhr.com. |
| `hirebridgeCompanies` | array | Cid number from recruit.hirebridge.com/v3/Jobs/list.aspx?cid=, e.g. 7780. |
| `trinetHireCompanies` | array | Company from app.trinethire.com/companies//jobs, e.g. 22943-x. |
| `polymerCompanies` | array | Company from jobs.polymer.co/, e.g. magnendo. |
| `goHireCompanies` | array | Board from jobs.gohire.io//, e.g. piersight-rfd9c90d. |
| `acquireTmTenants` | array | Tenant from .acquiretm.com, e.g. ecmd. |
| `harbourAtsTenants` | array | Tenant from .harbourats.com (e.g. aria.amal), e.g. aria.amal. |
| `sagePeopleSites` | array | Site from .my.salesforce-sites.com/recruit, e.g. peoplecore. |
| `silkRoadCompanies` | array | Company from jobs.silkroad.com//Careers, e.g. Colsa. |
| `paycorClientIds` | array | ClientId from recruitingbypaycor.com/career/CareerHome.action?clientId=, e.g. 8a7883d0900e460701902c92de2a0e43. |
| `getroNetworks` | array | Jobs board host of a VC network, e.g. jobs.a16z.com, e.g. jobs.a16z.com. |
| `appliTrackDistricts` | array | District from www.applitrack.com//onlineapp, e.g. ccsd. |
| `loxoAgencies` | array | Agency from app.loxo.co/, e.g. loxo. |
| `tribepadSites` | array | Site from .tribepad.com, e.g. twinkl. |
| `cezanneIntervieweBoards` | array | Board as /, from .intervieweb.it//en/career, e.g. cezanneondemand/bcha. |
| `networxBrands` | array | Brand from .current-vacancies.com, e.g. ymca. |
| `peopleAdminSites` | array | Site like uta.peopleadmin.com, e.g. uta.peopleadmin.com. |
| `gupyCompanies` | array | Company from .gupy.io, e.g. ambev. |
| `traffitCompanies` | array | Company from .traffit.com, e.g. traffit. |
| `radancySites` | array | Careers host, e.g. jobs.vinci.com/en (up to 5,000 jobs), e.g. jobs.vinci.com/en. |
| `phenomSites` | array | Careers host or company domain, e.g. jobs.cvshealth.com (up to 5,000 jobs), e.g. cvshealth.com. |
| `jibeSites` | array | Jibe (iCIMS career site) host, e.g. jobs.uhs.com (up to 5,000 jobs), e.g. jobs.uhs.com. |
| `paradoxSites` | array | Paradox career site host, e.g. jobs.harrishealth.org, e.g. jobs.harrishealth.org. |
| `taleoBusinessEditionLinks` | array | Taleo Business Edition careers link (...tbe.taleo.net/.../careers/v2/jobSearch?org=...&cws=...), e.g. https://phf.tbe.taleo.net/phf02/ats/careers/v2/jobSearch?org=COSTCO&cws=41. |
| `taleoCareerSections` | array | Taleo Enterprise career section (.taleo.net/careersection/), e.g. valero.taleo.net/careersection/2. |
| `paycomPortals` | array | Paycom portal key or careers link, e.g. https://www.paycomonline.net/v4/ats/web.php/portal/8B43E6E34C5D5C9AA3D07BB04DBEB909/career-page. |
| `adpCareerCenters` | array | ADP Workforce Now careers link or its cid, e.g. https://workforcenow.adp.com/mascsr/default/mdf/recruitment/recruitment.html?cid=070b2b3d-d077-4d73-b340-6055055056a6&ccId=19000101_000001&lang=en_US. |
| `recootyCompanies` | array | Company from jobs.recooty.com/, e.g. atom-com. |
| `catsCompanies` | array | Company from .catsone.com/careers, e.g. canadabread (CATS, used by US and Canadian staffing agencies). |
| `varbiEmployers` | array | Employer from .varbi.com, e.g. kth or ki (Swedish universities, regions and public bodies). |
| `governmentJobsAgencies` | array | Agency from www.governmentjobs.com/careers/, e.g. lacounty (NEOGOV, US cities, counties and states; every page is read). |
| `recruiterflowCompanies` | array | Company from recruiterflow.com//jobs, e.g. carguysinc (US staffing and recruiting firms). |
| `dvinciCompanies` | array | Company from .dvinci-easy.com, e.g. toom-baumarkt or weig (German employers). |
| `employmentHeroOrganisations` | array | Organisation id from employmenthero.com/.../organisations/, e.g. healthwiseorgau (Employment Hero: Australia, New Zealand, UK, Singapore, Malaysia, Canada). |
| `weRecruitCompanies` | array | Company from careers.werecruit.io/, e.g. conseil-et-expertise-du-sud (WeRecruit, French SMEs). |
| `beesiteTenants` | array | Tenant from api-.beesite.de, e.g. deutschebank (beesite by milch & zucker; every page is read). |
| `umantisBoards` | array | Board from recruitingapp-.umantis.com, e.g. recruitingapp-12705 or just 12705 (German, Swiss and Austrian employers; every page is read). |
| `jobApsAgencies` | array | Agency from www.jobapscloud.com/, e.g. MD (State of Maryland) or SJQ (San Joaquin County). |
| `scoutTalentCompanies` | array | Company from .applynow.net.au, e.g. floreyinstitute (Scout Talent, Australia, New Zealand, Canada). |
| `hrmosCompanies` | array | Company from hrmos.co/pages//jobs, e.g. moneyforward (HRMOS, Japan; every page is read). |
| `greetingHrSites` | array | Company from .career.greetinghr.com, e.g. kurly, or a company's own GreetingHR careers host, e.g. www.musinsacareers.com. |
| `herpCompanies` | array | Company from herp.careers/v1/, e.g. smartbank or kaminashi (HERP, Japanese startups). |
| `kekaCompanies` | array | Company from .keka.com/careers, e.g. cars24 or jupiter (Keka, India and the Gulf; salary and skills when published). |
| `schoolSpringBoards` | array | District from .schoolspring.com or .tedk12.com, e.g. slcschools (PowerSchool, US school districts; every page is read). |
| `talentLyftCompanies` | array | Company from .talentlyft.com, e.g. kpmg-bulgaria (TalentLyft, Croatia, Balkans, Central Europe). |
| `talentsoftSites` | array | Career site from .talent-soft.com, e.g. geodis-recrute or dc-careers (Cegid Talentsoft, France and Europe; every page is read). |
| `oleeoBoards` | array | Tenant from .tal.net, e.g. fco, or fco/2 for its second board (Oleeo, UK public sector, banks, graduate schemes; every page is read). |
| `vincereAgencies` | array | Agency from .vincere.io/careers, e.g. goldenkeys (Vincere, recruitment agencies, UK, Ireland, Asia-Pacific; every page is read, salary and description included). |
| `njoynBoards` | array | Board as CL/ from a clients.njoyn.com link, e.g. CL3/55227 for the City of Abbotsford (Njoyn by CGI, Canadian cities and universities). |
| `brassringSites` | array | Site as partnerid/siteid from a brassring.com TGnewUI link, e.g. 26173/5197 for Publix (IBM Kenexa BrassRing, large US employers; every page is read). |
| `jobsoidCompanies` | array | Company from .jobsoid.com, e.g. workatedge (Jobsoid, India, South-East Asia; description, salary and experience included). |
| `pandapeCompanies` | array | Company from .pandape.infojobs.com.br, e.g. carrefour or ifood (Pandapé by InfoJobs, Brazil and Latin America; every page is read). |
| `jobcanCompanies` | array | Company from recruit.jobcan.jp/, e.g. mos (Jobcan, Japan; every page is read, summary included). |
| `recruitisSites` | array | Career site from .jobs.recruitis.io, e.g. adastra (Recruitis, Czech Republic and Slovakia). |
| `jobtoolzCompanies` | array | Company from .jobtoolz.com, e.g. titeca (Jobtoolz, Belgium and the Netherlands). |
| `academicJobsOnlineEmployers` | array | Employer code from academicjobsonline.org/ajo/, e.g. BU for Boston University (Academic Jobs Online, universities and research institutes; department and deadline included). |
| `kulaCompanies` | array | Company from careers.kula.ai/, e.g. cashfree or rocketlane (Kula, India and US startups). |
| `reachmeeAttractSites` | array | Site from .attract.reachmee.com, e.g. apotek1 (ReachMee Attract, Norway and Sweden; region, category and deadline included). |
| `gestmaxSites` | array | Site from .gestmax.fr, e.g. antony or ansm-recrutement (Gestmax, France: local authorities, public bodies, companies; every page is read). |
| `quickinCompanies` | array | Company from jobs.quickin.io/, e.g. koin or cdludi (Quickin, Brazil; every page is read, salary, contract and description included). |
| `crelatePortals` | array | Portal from jobs.crelate.com/portal/, e.g. clayco (Crelate, US recruitment agencies and employers; every open job, description included). |
| `pcrecruiterBoards` | array | Board uid from www2.pcrecruiter.net/pcrbin/jobboard.aspx?uid=..., e.g. hcr.hcrjobs (PCRecruiter by Main Sequence, US staffing agencies and employers; every result page is read). |
| `bullhornBoards` | array | Career portal as /, e.g. 42/6VV91S, read from the agency's career site config (public-rest.bullhornstaffing.com/rest-services/). |
| `engageSites` | array | Site from .engageats.co.uk, e.g. barnsley (Engage ATS by Havas People, UK councils, police forces, schools and employers; every page is read, salary and closing date included). |
| `gr8peopleSites` | array | Career site from .workgr8.com or .gr8people.com, e.g. randstadnorthamerica (GR8 People, US employers and staffing firms; every open job, description and pay range included). |
| `reachSites` | array | Site key from .reach-ats.com, the public vacancy feed behind the employer's career site (Reach ATS, UK employers; every live vacancy, salary and hours included). |
| `hrworksCompanies` | array | companyId from jobapplication.hrworks.de/?companyId=..., e.g. a4c538d (HRworks, German small and mid-size employers; every job of the list, category, level and place included). |
| `peoplebankSites` | array | Client from peoplebank.com/pb3/corporate/, e.g. jksrestaurants (PeopleBank, UK hospitality, retail and construction employers; every vacancy, department and closing date included). |
| `sensehqSites` | array | Career site from .sensehq.com/careers, e.g. ab-inbev-gcc (SenseHQ, India and US employers; every page, description and experience range included). |
| `bizneoSites` | array | Job board host from .bizneo.cloud/jobs, e.g. jobs.abeienergy.bizneo.cloud (Bizneo ATS, Spain, Portugal and Latin America; every page of the board, place and work mode included). |
| `joblinkApplyCompanies` | array | Company from .joblinkapply.com (US hourly hiring), e.g. fcssecurity. |
| `clearCompanyCompanies` | array | Company from apply.clearcompany.com/, e.g. lcmh. |
| `deelCompanies` | array | Company from jobs.deel.com/, e.g. klarna. |
| `talentechCompanies` | array | Company from jobs.talentech.com/ (Nordics), e.g. surgicalscience. |
| `onShiftCompanies` | array | Company from .employ.onshift.com (US senior care), e.g. wesbury. |
| `jobtrainBoards` | array | Board from www.jobtrain.co.uk/ (UK public sector), e.g. iomgovjobs. |
| `talentLinkSites` | array | Lumesse TalentLink career host, e.g. mubeacareers.recruitmentplatform.com, e.g. mubeacareers.recruitmentplatform.com. |
| `eploySites` | array | Site like altradweb.eploy.net (UK), e.g. altradweb.eploy.net. |
| `talos360Sites` | array | Site like ukas.talosats-careers.com (UK), e.g. ukas.talosats-careers.com. |
| `applicantStackCompanies` | array | Company from .applicantstack.com (Swipeclock / WorkforceHub), e.g. swipeclock. |
| `onlyfyCompanies` | array | Company from .onlyfy.jobs (onlyfy / Prescreen, DACH), e.g. prescreen. |
| `careerPlugCompanies` | array | Company from .careerplug.com (US franchises), e.g. sportclips. |
| `includeDescription` | boolean | Add the full job description (plain text), salary, contract type, workplace type and apply link when the system publishes them, plus facts read from the text: years of experience, skills, visa sponsorship, degree. Default: `true`. |
| `includeCompanyProfile` | boolean | Add each company's industry, employee count, size band (1-10 ... 10,001+), headquarters and founding year, from Wikidata by the company's website. Default: `true`. |
| `industries` | array | Keep only companies whose industry contains one of these words (software, retail, insurance, financial...). |
| `companySizes` | array | Keep only companies of these sizes (employees). |
| `maxTotalChargeUsd` | number | Hard maximum amount that this run may charge. |
| `previousJobs` | array | Optional. |
| `currentJobs` | array | Optional. |
| `monitorEnabled` | boolean | The first monitored run stores a free baseline. Default: `false`. |
| `monitorId` | string | Pins the persistent baseline to a name of your choice. |
| `sources` | array | Declare every upstream source before this run. Default: `[{"name": "Customer-authorized input", "authorization": "cus`. |
| `keywords` | array | Keep only jobs whose title, department, company or location contains one of these words. Default: `["engineer"]`. |
| `excludeKeywords` | array | Drop jobs matching any of these words, e.g. intern, senior, sales. |
| `locations` | array | Keep only jobs whose location contains one of these, e.g. Berlin, United Kingdom. |
| `remoteOnly` | boolean | Keep only roles whose location says remote, anywhere or distributed. Default: `false`. |
| `postedAfter` | string | Keep only jobs posted on or after this date (YYYY-MM-DD). |
| `employmentTypes` | array | Keep only these contract types (read from the job system's own field, the title, or a clear phrase in the text). |
| `workArrangements` | array | Keep only these work arrangements. |
| `countries` | array | Keep only jobs in these countries: names or 2-letter codes (United States, US, Germany, DE...). |
| `excludeTitleKeywords` | array | Drop jobs whose TITLE has any of these words (e.g. senior, intern, manager), even if the description mentions them. |
| `excludeCompanies` | array | Drop jobs from these companies (part of the name is enough). |
| `excludeLocations` | array | Drop jobs whose location contains any of these words (e.g. India, Remote - EMEA). |
| `departments` | array | Keep only these departments or teams (e.g. Engineering, Sales). |
| `excludeAgencies` | boolean | Drop jobs posted by staffing or recruitment agencies for a client. Default: `false`. |
| `onlyWithSalary` | boolean | Keep only jobs that publish a pay range (as numbers, with the pay period and a yearly equivalent). Default: `false`. |
| `minYearlySalary` | integer | Keep only jobs paying at least this much per year (hourly, daily and monthly pay converted to yearly). |
| `postedWithin` | string | Keep only jobs posted in this window. |
| `maxYearlySalary` | integer | Drop jobs whose yearly pay starts above this (hourly, daily and monthly pay converted to yearly). |
| `jobFunctions` | array | Keep only these job families, read from the title (Engineering, Sales, Data & AI...). |
| `seniorities` | array | Keep only these levels, read from the title. |
| `skills` | array | Keep only jobs asking for at least one of these skills (read from the description, or the title), e.g. Python, Salesforce, SQL. |
| `excludeSkills` | array | Drop jobs asking for any of these skills. |
| `visaSponsorship` | string | Keep only jobs whose description says this about visa or work-permit sponsorship. |
| `maxExperienceYears` | integer | Drop jobs asking for more years of experience than this (jobs that ask for none are kept). |
| `descriptionKeywords` | array | Keep only jobs whose title or description contains one of these words. |
| `excludeDescriptionKeywords` | array | Drop jobs whose title or description contains any of these words, e.g. clearance, commission only. |
| `languages` | array | Keep only postings written in these languages (read from the text). |
| `onlyCompanies` | array | With "search all companies": keep only jobs of companies whose name contains one of these words. |
| `onlyNewJobs` | boolean | Deliver only the jobs this same search has not delivered before (remembered in your own Apify account). Default: `false`. |
| `memoryName` | string | Give the 'only new jobs' memory a name to share it between tasks or keep it when you change the search. |

## Example output

A row as shown in the Actor's README:

```json
{
  "source_url": "https://jobs.ashbyhq.com/ramp/2a4968ae-220c-471b-b890-a011de570bbb",
  "title": "Software Engineer, Bill Pay & Procurement",
  "company": "ramp",
  "location": "New York, NY (HQ)",
  "department": "Engineering",
  "posted_at": "2025-10-29T20:06:15.084+00:00",
  "source": "ashby",
  "salary": "$168K – $275.1K • Offers Equity",
  "job_id": "2a4968ae-220c-471b-b890-a011de570bbb",
  "description": "ABOUT RAMP\n\nRamp is building the smart infrastructure for finance teams, embedded in the transaction flow of every dollar a business spen...",
  "employment_type": "FullTime",
  "workplace_type": "remote",
  "apply_url": "https://jobs.ashbyhq.com/ramp/2a4968ae-220c-471b-b890-a011de570bbb/application",
  "function": "Engineering",
  "seniority": "Mid",
  "is_remote": false,
  "posted_within_days": 359,
  "is_recent": false,
  "experience_years": 3,
  "skills": [
    "Python",
    "SQL"
  ],
  "salary_min": 168000,
  "salary_max": 275100,
  "salary_currency": "USD",
  "record_id": "027593ffeed76d350d99d1c0",
  "change_type": "new",
  "why_it_matters": "New job posting: Software Engineer, Bill Pay & Procurement at ramp — a hiring signal."
}
```

## Run it from Python

```python
from apify_client import ApifyClient

client = ApifyClient("<YOUR_APIFY_TOKEN>")
run = client.actor("om_kh/ats-jobs-api").call(run_input={
    "companyDomains": [
        "stripe.com",
        "figma.com"
    ],
    "greenhouseBoards": [
        "stripe",
        "airbnb"
    ],
    "leverCompanies": [
        "spotify"
    ],
    "ashbyBoards": [
        "ramp"
    ]
})
for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(item)
```

## Run it with cURL

```bash
curl -X POST "https://api.apify.com/v2/acts/om_kh~ats-jobs-api/run-sync-get-dataset-items?token=<YOUR_APIFY_TOKEN>" \
  -H "Content-Type: application/json" \
  -d '{"companyDomains": ["stripe.com", "figma.com"], "greenhouseBoards": ["stripe", "airbnb"], "leverCompanies": ["spotify"], "ashbyBoards": ["ramp"]}'
```

## Use it from an AI agent (MCP)

Connect Claude, Cursor or any MCP client to `https://mcp.apify.com` and add `om_kh/ats-jobs-api` as a tool.

Full documentation, pricing and the latest changes: [ATS Jobs API - 123 ATS: Greenhouse, Lever, Workday Jobs](https://apify.com/om_kh/ats-jobs-api).
