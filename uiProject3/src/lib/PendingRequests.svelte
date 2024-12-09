<script>
    let showRequests = false; // State to track visibility of the requests box
  
    // Sample pending requests (can be dynamically loaded from a server or store)
    let pendingRequests = [
      { id: 1, requestor: 'Arline Wallace', status: 'Pending' },
      { id: 2, requestor: 'Carly Huynh', status: 'Pending' },
      { id: 3, requestor: 'Santo Obrien', status: 'Pending' },
    ];
  
    // Toggle the visibility of the request list
    function toggleRequests() {
      showRequests = !showRequests;
    }
  
    // Approve request logic
    function approveRequest(id) {
      const request = pendingRequests.find(req => req.id === id);
      if (request) {
        request.status = 'Approved';
      }
    }
  
    // Reject request logic
    function rejectRequest(id) {
      const requestIndex = pendingRequests.findIndex(req => req.id === id);
      if (requestIndex !== -1) {
        pendingRequests.splice(requestIndex, 1);
      }
    }
  </script>
  
  <!-- Button to toggle the visibility of pending requests -->
  <div class="requests-toggle">
    <button on:click={toggleRequests} aria-label={showRequests ? 'Hide pending requests' : 'Show pending requests'}>
      {showRequests ? 'Hide Pending Requests' : 'Show Pending Requests'}
    </button>
  </div>
  
  {#if showRequests}
    <div class="requests-box visible">
      <h3>Pending Requests</h3>
      {#if pendingRequests.length === 0}
        <p>No pending requests.</p>
      {:else}
        <ul class="requests-list">
          {#each pendingRequests as request (request.id)}
            <li class="request-item">
              <div class="request-details">
                <p><strong>{request.requestor}</strong> is requesting a skill swap.</p>
                <span class="request-status">{request.status}</span>
              </div>
              {#if request.status === 'Pending'}
                <div class="request-actions">
                  <button on:click={() => approveRequest(request.id)} aria-label={`Approve request from ${request.requestor}`}>Approve</button>
                  <button on:click={() => rejectRequest(request.id)} aria-label={`Reject request from ${request.requestor}`}>Reject</button>
                </div>
              {/if}
            </li>
          {/each}
        </ul>
      {/if}
    </div>
  {/if}
  
  <style>
    .requests-toggle {
      position: fixed;
      bottom: 20px;
      right: 20px;
      padding: 16px;
      z-index: 100;
    }
  
    .requests-toggle button {
      background-color: #3fb5d2;
      color: white;
      border: none;
      border-radius: 8px;
      padding: 10px 20px;
      font-size: 1rem;
      cursor: pointer;
      transition: background-color 0.3s ease;
    }
  
    .requests-toggle button:hover {
      background-color: #3f5bbb;
    }
  
    .requests-box {
      position: fixed;
      bottom: 80px;
      right: 20px;
      width: 300px;
      border: 1px solid #ddd;
      border-radius: 8px;
      background-color: #fff;
      box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
      padding: 16px;
      opacity: 0;
      transform: translateY(10px);
      transition: opacity 0.3s ease, transform 0.3s ease;
      z-index: 100;
      max-height: 400px;
      overflow-y: auto;
    }
  
    .requests-box.visible {
      opacity: 1;
      transform: translateY(0);
    }
  
    .requests-list {
      list-style: none;
      padding: 0;
      margin: 0;
    }
  
    .request-item {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 10px;
      border-bottom: 1px solid #eee;
      transition: background-color 0.3s ease;
    }
  
    .request-item:hover {
      background-color: #f1f1f1;
    }
  
    .request-details {
      display: flex;
      flex-direction: column;
    }
  
    .request-status {
      font-weight: bold;
      color: #3fb5d2;
    }
  
    .request-actions {
      display: flex;
      gap: 8px;
    }
  
    .request-actions button {
      background-color: #ffbd59;
      color: white;
      border: none;
      border-radius: 4px;
      padding: 6px 12px;
      cursor: pointer;
      font-size: 0.9rem;
      transition: background-color 0.3s ease;
    }
  
    .request-actions button:hover {
      background-color: #d32f2f;
    }
  
    .request-actions button:disabled {
      background-color: #ccc;
      cursor: not-allowed;
    }
  
    p {
      font-size: 1rem;
      margin: 8px 0;
    }
  
    .request-status {
      color: #00b5b8;
    }
  
    .request-actions button:disabled {
      background-color: #ddd;
    }
  
    @media (max-width: 600px) {
      .requests-box {
        right: 10px;
        bottom: 80px;
        width: 90%;
      }
    }
  </style>
  